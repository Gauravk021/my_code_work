public List<DataInsights> findAllDataInsightsByBranchId(long branchId, int offset, int pageSize) {
    logger.info("Inside findAllDataInsightsByBranchId: branchId = {}, offset = {}, pageSize = {}",
            branchId, offset, pageSize);

    Pageable p = (Pageable) PageRequest.of(offset, pageSize);

    // this reuses the same repo call used in findRelationshipsBySearch()
    return dataInsightsRepository.findByBranchNumber(branchId, p);
}. 




