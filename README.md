public List<DataInsights> findAllDataInsightsByBranchId(long branchId, int offset, int pageSize) {
    logger.info("Inside findAllDataInsightsByBranchId: branchId = {}, offset = {}, pageSize = {}",
            branchId, offset, pageSize);

    Pageable p = (Pageable) PageRequest.of(offset, pageSize);

    // this reuses the same repo call used in findRelationshipsBySearch()
    return dataInsightsRepository.findByBranchNumber(branchId, p);
}. @Operation(
        summary = "Get Insights by BranchID",
        description = "Returns list of data insights based on provided branchId"
)
@PostMapping("/get-insights-by-branchId")
public List<DataInsights> getALLInsightsByBranchId(
        @Valid @RequestParam(name = "branchId") Long branchId,
        @RequestParam(name = "offset", required = true) int offset,
        @RequestParam(name = "pageSize", required = true) int pageSize,
        final HttpServletRequest request) throws Exception {

    List<DataInsights> insights = null;

    final String methodName = "getALLInsightsByBranchId";
    final String userId = extractUserId(request);    // same helper you use in other methods
    final Long brId = branchId;

    try {
        // REQUEST log
        log.info("LunaPanel request: method={}, branchId={}, userId={}, offset={}, pageSize={}",
                methodName, brId, userId, offset, pageSize);

        // actual service call
        insights = dataInsightsService.findAllDataInsightsByBranchId(branchId, offset, pageSize);

        // SUCCESS log
        log.info("LunaPanel success: method={}, branchId={}, userId={}, resultCount={}",
                methodName, brId, userId, (insights != null ? insights.size() : 0));

    } catch (Exception e) {
        // FAILURE log
        log.error("LunaPanel failed: method={}, branchId={}, userId={}",
                methodName, brId, userId, e);

        handleCommonException(request, e);
    }

    return insights;
}






