@GetMapping("/get-insights-by-status")
public List<DataInsights> getALLRelationship(
    @Valid @RequestParam(name = "relationshipID") Long relationshipID,
    @Valid @RequestParam(name = "status", required = true) String status,
    @RequestParam(name = "offset", required = true) int offset,
    @RequestParam(name = "pageSize", required = true) int pageSize,
    HttpServletRequest request) throws Exception {

    List<DataInsights> insights = null;
    final String methodName = "get-insights-by-status";
    String userId = extractUserId(request); // 👈 this is the helper we added
    Long faId = null; // 👈 this endpoint doesn’t have faNumber param

    try {
        // 👇 this is the REQUEST log
        log.info("LunaPanel request: method={}, faId={}, userId={}, relationshipId={}, status={}, offset={}, pageSize={}",
                methodName, faId, userId, relationshipID, status, offset, pageSize);

        insights = dataInsightsService.getInsightsByStatus(relationshipID, status, offset, pageSize);

        // 👇 this is the SUCCESS log
        log.info("LunaPanel success: method={}, faId={}, userId={}, relationshipId={}, resultCount={}",
                methodName, faId, userId, relationshipID, (insights != null ? insights.size() : 0));
    } catch (Exception e) {
        // 👇 this is the FAILURE log
        log.error("LunaPanel failed: method={}, faId={}, userId={}, relationshipId={}",
                methodName, faId, userId, relationshipID, e);
        handleCommonException(request, e);
    }
    return insights;
}