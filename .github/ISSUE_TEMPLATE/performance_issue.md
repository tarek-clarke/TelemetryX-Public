name: Performance Issue
description: Report high overhead or performance degradation caused by the overlay.
labels: [performance]
body:
  - type: input
    id: spec
    attributes:
      label: System Specs
      description: GPU, CPU, and RAM.
    validations:
      required: true
  - type: input
    id: game
    attributes:
      label: Game/App Affected
      description: Which application is showing performance loss?
  - type: textarea
    id: overhead_desc
    attributes:
      label: Performance Impact
      description: Describe the impact (e.g., "10% FPS drop", "stuttering every 5 seconds").
    validations:
      required: true
