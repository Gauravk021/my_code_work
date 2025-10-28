private String extractUserId(HttpServletRequest request) {
  // 1️⃣ Some tests pass null request, so handle that
  if (request == null) {
    return null;
  }

  // 2️⃣ Try from security principal (login user)
  try {
    if (request.getUserPrincipal() != null) {
      return request.getUserPrincipal().getName();
    }
  } catch (Exception ignore) {}

  // 3️⃣ Try from the header (sysId)
  try {
    String sysId = request.getHeader("sysId");
    if (sysId != null && !sysId.isEmpty()) {
      return sysId;
    }
  } catch (Exception ignore) {}

  // 4️⃣ Try from dataInsightsService (fallback)
  try {
    if (dataInsightsService != null) {
      User user = dataInsightsService.findUserDetails();
      if (user != null && user.getPeopleKey() != null) {
        return user.getPeopleKey();
      }
    }
  } catch (Exception ignore) {}

  // 5️⃣ If nothing works, return null
  return null;
}