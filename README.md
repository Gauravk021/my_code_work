public List<DataInsights> findAllDataInsightsByBranchId(long branchId, int offset, int pageSize) {

    logger.info("Inside findAllDataInsightsByBranchId: branchId = {}, offset = {}, pageSize = {}",
            branchId, offset, pageSize);

    Pageable p = (Pageable) PageRequest.of(offset, pageSize);

    // reuse the same repository method as search-by-branchId
    return dataInsightsRepository.findByBranchNumber(branchId, p);
}