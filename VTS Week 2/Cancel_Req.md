## Cancel Request Flowchart

flowchart TD
  A([Start]) --> B[Employee Login VTS Portal System]
  B --> C[System Show Vacation Requests]
  C --> D[Employee Select Approved Req]

  D --> E{Future OR\nPrevious 5 Business Days}

  %% Future path
  E -->|Future| F[Confirm Cancellation]
  F --> G{Confirmed?}
  G -->|YES| H[State Updated to Cancelled]
  H --> I[Return Balance To Employee]
  I --> J[Send Update To Manager]
  J --> K([End])
  G -->|NO| L[Abort Cancel - Not Confirmed]
  L --> K

  %% Previous 5 BD path
  E -->|Previous 5 BD| M[Enter Cancellation Explanation]
  M --> N{Reason Provided?}
  N -->|YES| O[State Updated to Cancelled]
  O --> P[Return Balance To Employee]
  P --> Q[Send Update To Manager]
  Q --> K
  N -->|NO| R[Abort Cancel - Not Confirmed]
  R --> K
