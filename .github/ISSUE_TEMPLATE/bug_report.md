name: Bug Report
description: Report a bug to help us improve TelemetryX.
labels: [bug]
body:
  - type: markdown
    attributes:
      value: |
        Thanks for taking the time to fill out this bug report!
  - type: input
    id: system_info
    attributes:
      label: System Information
      placeholder: OS (e.g., Windows 11), GPU (e.g., RTX 3080), Driver version.
    validations:
      required: true
  - type: textarea
    id: reproduction
    attributes:
      label: Reproduction Steps
      description: How did you encounter this bug?
    validations:
      required: true
  - type: textarea
    id: expected_behavior
    attributes:
      label: Expected Behavior
      placeholder: What should have happened?
  - type: textarea
    id: actual_behavior
    attributes:
      label: Actual Behavior
      placeholder: What actually happened?
  - type: checkboxes
    id: terms
    attributes:
      label: Code of Conduct
      description: By submitting this issue, you agree to follow our Code of Conduct.
      options:
        - label: I agree to follow this project's Code of Conduct.
          required: true
