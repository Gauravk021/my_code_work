// If TLE clearly says account/security not found, do not convert it to Vendor Maintenance.
if (StringUtils.isNotBlank(errAry[0]) && "NF".equals(errAry[0])) {
    log.warn("{} ACCOUNT NOT FOUND ON TLE: {}", METHOD_NAME, buildExceptionMessage(accountNumber, message));
    throw new TleAccountNotFoundException("Error from TLE " + buildExceptionMessage(accountNumber, message));
}

// For real TLE/vendor errors, show maintenance only during outage window.
if (isTLEOutageWindow()) {
    log.error("{} [Account# {}] TLE Maintenance window", METHOD_NAME, accountNumber);
    throw new TleMaintenanceException(
            "TLE Maintenance window. No data available for account " + accountNumber);
}

if (StringUtils.isNotBlank(errAry[0])) {
    if ("REQUEST_ERROR".equals(errAry[0]) || "TLE_ERROR".equals(errAry[0])) {
        log.error("{} {}", METHOD_NAME, buildExceptionMessage(accountNumber, message));
        log.error("Account {} Request XML:\n{}\n\nResponse XML:\n{}", accountNumber, requestXML, responseXML);
        throw new TleServiceException("Error from TLE " + buildExceptionMessage(accountNumber, message));
    } else {
        log.warn("{} error code NOT FOUND on Broadridge constants file errorCode={}", METHOD_NAME, errorCode);
    }
}