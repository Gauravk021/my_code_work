// --- helper: find a user id for logging ---
private String extractUserId(HttpServletRequest request) {
  // 1) try security principal (if SSO/JWT is used)
  if (request.getUserPrincipal() != null) {
    return request.getUserPrincipal().getName();
  }
  // 2) try the existing header you already use in this controller
  String sysId = request.getHeader("sysId");
  if (sysId != null && !sysId.isEmpty()) {
    return sysId;
  }
  // 3) fallback to your existing user lookup
  try {
    User user = dataInsightsService.findUserDetails();
    if (user != null && user.getPeopleKey() != null) {
      return user.getPeopleKey();
    }
  } catch (Exception ignore) {}
  return null;
}