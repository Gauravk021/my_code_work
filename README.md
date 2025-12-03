@Operation(
        summary = "Get Insights by BranchID",
        description = "Returns list of data insights based on provided branchId"
)
@PostMapping("/get-insights-by-branchId")
public List<DataInsights> getALLInsightsByBranchId(
        @Valid @RequestParam(name = "branchId") Long branchId,
        @RequestParam(name = "offset", required = true) int offset,
        @RequestParam(name = "pageSize", required = true) int pageSize,
        final HttpServletRequest request) {

    List<DataInsights> insights = null;

    try {
        final String methodName = "getALLInsightsByBranchId";

        // REQUEST log (similar style to others)
        log.debug(LunaConstants.ENTERING_METHOD, methodName, request);
        log.info("LunaPanel request: method={}, branchId={}, offset={}, pageSize={}",
                methodName, branchId, offset, pageSize);

        // SERVICE call
        insights = dataInsightsService.findAllDataInsightsByBranchId(branchId, offset, pageSize);

        // SUCCESS log
        log.info("LunaPanel success: method={}, branchId={}, resultCount={}",
                methodName, branchId, (insights != null ? insights.size() : 0));

    } catch (Exception e) {
        // FAILURE handling
        log.error("LunaPanel failed: method={}, branchId={}", "getALLInsightsByBranchId", branchId, e);
        handleCommonException(request, e);
    }

    return insights;
}