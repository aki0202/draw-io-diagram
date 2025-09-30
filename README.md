## Order Journey Diagram

```mermaid
flowchart TD
    RF["RF (ISP)\nPostal Redirect"]
    CO["Category Order"]
    SM["Subscription Manager (SM)\nCentral Hub"]

    %% Branches from SM
    PLSM["PLSM"]
    FOSP["Fibre Optic SP"]
    OSS["BigLynx System (OSS)"]
    DB["DATABASE\n- Equipment Dispatch\n- Kenton (APS)\n- Manual Tickets\n- Orders & Migrations"]
    PAY["MT (Payments)\nStripe / GoCardless / BACS"]
    CBS["Billing System CBS\nContinuous Billing"]
    OFNL["Postcode DP OFNL"]
    Vendors["TalkTalk / CityFibre"]

    %% Parallel Processes under SM
    SC["Selfcare (End User)"]
    CC["Customer Care (ISP)"]
    TICK["Ticketing (OPS / ISP)"]
    CRM["CRM (OPS / ISP)"]
    KCI["KCI (Keep Customer Informed)"]

    %% Main flow
    RF --> CO --> SM
    SM --> PLSM
    SM --> FOSP
    SM --> OSS
    SM --> DB
    SM --> PAY --> CBS
    SM --> CBS
    SM --> OFNL --> Vendors

    %% Parallel under SM
    SM --> SC
    SM --> CC
    SM --> TICK
    SM --> CRM
    SM --> KCI
