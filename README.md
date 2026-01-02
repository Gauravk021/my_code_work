@NotBlank(message = "ruleValue is required")
@Pattern(
    regexp = "^[0-9]+$",
    message = "ruleValue must contain only numbers"
)
private String ruleValue;