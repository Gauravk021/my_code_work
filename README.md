@Operation(summary = "Get Insights by RelationshipID", description = "Returns list of data insights based on provided relationshipID")
@PostMapping("/get-insights-by-relationshipID")
public List<DataInsights> getInsightsByRelationshipID(
    @Valid @RequestParam(name = "relationshipID") Long relationshipID,
    HttpServletRequest request) throws Exception {

    List<DataInsights> insights = null;
    final String methodName = "getInsightsByRelationshipID";
    String userId = extractUserId(request);
    Long faId = null; // this endpoint doesn't have faNumber

    try {
        // REQUEST log
        log.info("LunaPanel request: method={}, faId={}, userId={}, relationshipId={}",
                 methodName, faId, userId, relationshipID);

        insights = dataInsightsService.findInsightsByRelationshipID(relationshipID);

        // SUCCESS log
        log.info("LunaPanel success: method={}, faId={}, userId={}, relationshipId={}, resultCount={}",
                 methodName, faId, userId, relationshipID, (insights != null ? insights.size() : 0));
    } catch (Exception e) {
        // FAILURE log
        log.error("LunaPanel failed: method={}, faId={}, userId={}, relationshipId={}",
                  methodName, faId, userId, relationshipID, e);
        handleCommonException(request, e);
    }

    return insights;
}