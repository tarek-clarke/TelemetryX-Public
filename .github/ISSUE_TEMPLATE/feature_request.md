name: Feature Request
description: Suggest a new feature or improvement for TelemetryX.
labels: [enhancement]
body:
  - type: textarea
    id: feature_desc
    attributes:
      label: Feature Description
      description: A clear and concise description of what you want to happen.
    validations:
      required: true
  - type: textarea
    id: use_case
    attributes:
      label: Use Case
      description: Why is this feature useful? Who is it for?
    validations:
      required: true
  - type: textarea
    id: alternatives
    attributes:
      label: Alternatives Considered
      description: Have you considered any other ways to achieve this?
