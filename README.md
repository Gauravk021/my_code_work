@PostMapping("/get-insights-by-faNumber-relationshipID")
public List<DataInsights> getAllInsightsByFaNumberAndRelationshipID(
    @Valid @RequestParam(name = "faNumber") long faNumber,
    @Valid @RequestParam(name = "relationshipID") long relationshipID,
    HttpServletRequest request) throws Exception {

    List<DataInsights> insights = null;
    final String methodName = "getAllInsightsByFaNumberAndRelationshipID";
    String userId = extractUserId(request); // ✅ new helper you created
    Long faId = faNumber;

    try {
        // 🔹 REQUEST log
        log.info("LunaPanel request: method={}, faId={}, userId={}, relationshipId={}",
                 methodName, faId, userId, relationshipID);

        insights = dataInsightsService.findAllDataInsightsByFaNumberAndRelationshipID(faNumber, relationshipID);

        // 🔹 SUCCESS log
        log.info("LunaPanel success: method={}, faId={}, userId={}, relationshipId={}, resultCount={}",
                 methodName, faId, userId, relationshipID, (insights != null ? insights.size() : 0));

    } catch (Exception e) {
        // 🔹 FAILURE log
        log.error("LunaPanel failed: method={}, faId={}, userId={}, relationshipId={}",
                  methodName, faId, userId, relationshipID, e);
        handleCommonException(request, e);
    }

    return insights;
}