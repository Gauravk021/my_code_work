@NotBlank(message = "ruleParameter is required")
@Pattern(
    regexp = "^[a-zA-Z0-9_-]+$",
    message = "ruleParameter must contain only letters, numbers, _ or -"
)
private String ruleParameter;