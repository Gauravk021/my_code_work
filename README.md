@PostMapping("/createInsightRuleDrools")
public ResponseEntity<ResponseStructure> createInsightRuleDrools(
        @Valid @RequestBody InsightsRulesModel rulesRequest,
        BindingResult bindingResult) {

    logger.info("Inside createInsightRuleDrools()");

    // ✅ STEP 1: Validation check
    if (bindingResult.hasErrors()) {
        String errorMessage = bindingResult.getFieldErrors()
                .stream()
                .map(err -> err.getField() + " : " + err.getDefaultMessage())
                .collect(Collectors.joining(", "));

        return ResponseEntity.badRequest().body(
                new ResponseStructure("Error", 400, errorMessage)
        );
    }

    // ✅ STEP 2: Call service only if validation passed
    try {
        insightsRulesService.createInsightRuleDrools(rulesRequest);

        return ResponseEntity.ok(
                new ResponseStructure(
                        "success",
                        200,
                        "Drool Insight rule has been created successfully"
                )
        );

    } catch (IOException e) {
        logger.error("Error generating DRL file", e);

        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body(
                new ResponseStructure(
                        "Error",
                        500,
                        "Error generating DRL file"
                )
        );
    }
}