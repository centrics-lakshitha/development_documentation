# 📊 LabLink Complete Flowchart Guide

<div align="center">

![Odoo](https://img.shields.io/badge/Odoo-18.0-714B67?style=for-the-badge&logo=odoo&logoColor=white)
![Flowcharts](https://img.shields.io/badge/Complete-Flowcharts-success?style=for-the-badge)

**Comprehensive Flowchart Diagrams for All LabLink Custom Developments**

*Complete visual guide from system configuration to daily operations*

</div>

---

## 📋 Table of Contents

1. [System Setup & Configuration Flowchart](#-system-setup--configuration-flowchart)
2. [Master Data Configuration Flowchart](#-master-data-configuration-flowchart)
3. [Partner Management Complete Flowchart](#-partner-management-complete-flowchart)
4. [Product Management Complete Flowchart](#-product-management-complete-flowchart)
5. [CRM to Sales Complete Flowchart](#-crm-to-sales-complete-flowchart)
6. [Sales Order Validation Complete Flowchart](#-sales-order-validation-complete-flowchart)
7. [Complete Business Process Flowchart](#-complete-business-process-flowchart)
8. [Daily Operations Flowchart](#-daily-operations-flowchart)
9. [Troubleshooting Decision Flowchart](#-troubleshooting-decision-flowchart)

---

## 🚀 System Setup & Configuration Flowchart

### Complete Initial Setup Process

```mermaid
flowchart TB
    Start([Start: New LabLink System]) --> InstallModules

    subgraph InstallModules[" 📦 STEP 1: Module Installation "]
        direction TB
        M1[Install centrics_approval_process_base] --> M2[Install centrics_multi_level_approval_process]
        M2 --> M3[Install bi_product_brand]
        M3 --> M4[Install one2many_sequence_sf]
        M4 --> M5[Install lablink_base_extend]
        M5 --> M6[Install centrics_partner_multi_approval_process]
        M6 --> M7[Install centrics_product_approval_process]
        M7 --> M8[Install lablink_crm_extend]
        M8 --> M9[Install lablink_custom_development]
        M9 --> M10[Install local_tax_config]
        M10 --> M11[Install lablink_sales_extend]
        M11 --> M12[Install sales_validations]
        M12 --> M13[Install lablink_mail_thread]
    end

    InstallModules --> SecuritySetup

    subgraph SecuritySetup[" 👥 STEP 2: Security & Users "]
        direction TB
        S1[Create User Accounts] --> S2[Assign Base Access Rights]
        S2 --> S3{Assign to Groups}

        S3 --> S3a[Multi Approval Manager]
        S3 --> S3b[Partner Approvers]
        S3 --> S3c[Product Approvers]
        S3 --> S3d[Sales Approvers<br/>GP/Credit/Payment/All]
        S3 --> S3e[Show Invoice Margin]

        S3a --> S4[Security Setup Complete ✓]
        S3b --> S4
        S3c --> S4
        S3d --> S4
        S3e --> S4
    end

    SecuritySetup --> ApprovalConfig

    subgraph ApprovalConfig[" ✅ STEP 3: Approval Configuration "]
        direction TB
        A1[Settings → Multi Approvals] --> A2{Configure Partner Approval}

        A2 --> A2a[Set Approval Levels: 1/2/3]
        A2a --> A2b[Add Level 1 Users]
        A2b --> A2c{Need Level 2?}
        A2c -->|Yes| A2d[Add Level 2 Users]
        A2c -->|No| A2e[Set Approval Method:<br/>All/Any per level]
        A2d --> A2f{Need Level 3?}
        A2f -->|Yes| A2g[Add Level 3 Users]
        A2f -->|No| A2e
        A2g --> A2e

        A2e --> A3{Configure Product Approval}

        A3 --> A3a[Set Approval Levels: 1/2/3]
        A3a --> A3b[Add Approver Users]
        A3b --> A3c[Set Approval Methods]

        A3c --> A4[Approval Config Complete ✓]
    end

    ApprovalConfig --> PartnerSettings

    subgraph PartnerSettings[" 🏢 STEP 4: Partner Settings "]
        direction TB
        P1[Settings → General Settings] --> P2[Partner Document Validate Period]
        P2 --> P3[Enter Days: 14 default]
        P3 --> P4[Partner Settings Complete ✓]
    end

    PartnerSettings --> MasterData

    subgraph MasterData[" 📋 STEP 5: Master Data Setup "]
        direction TB
        MD1{Create Master Data} --> MD1a[Business Nature]
        MD1 --> MD1b[Customer Type SSCL]
        MD1 --> MD1c[Product Brands]
        MD1 --> MD1d[Product Categories<br/>+ Codes + GP Margins]
        MD1 --> MD1e[Availability Options]
        MD1 --> MD1f[Sale Order Priorities]

        MD1a --> MD2[Master Data Complete ✓]
        MD1b --> MD2
        MD1c --> MD2
        MD1d --> MD2
        MD1e --> MD2
        MD1f --> MD2
    end

    MasterData --> TaxConfig

    subgraph TaxConfig[" 💰 STEP 6: Tax Configuration "]
        direction TB
        T1[Accounting → Taxes] --> T2{Create Tax Types}

        T2 --> T2a[VAT 18%<br/>VAT Type: vat]
        T2 --> T2b[SVAT 8%<br/>VAT Type: svat]
        T2 --> T2c[GST Taxes<br/>VAT Type: gst]
        T2 --> T2d[Other/Non-VAT<br/>VAT Type: other]

        T2a --> T3[Tax Config Complete ✓]
        T2b --> T3
        T2c --> T3
        T2d --> T3
    end

    TaxConfig --> SalesValidation

    subgraph SalesValidation[" 🔍 STEP 7: Sales Validations "]
        direction TB
        SV1[Settings → Sales] --> SV2{Enable Validations}

        SV2 --> SV2a{GP Margin Validation?}
        SV2a -->|Yes| SV2a1[✓ Enable<br/>Set Company GP Margin %]
        SV2a -->|No| SV2a2[Skip]

        SV2 --> SV2b{Credit Limit Validation?}
        SV2b -->|Yes| SV2b1[✓ Enable]
        SV2b -->|No| SV2b2[Skip]

        SV2 --> SV2c{Payment Terms Validation?}
        SV2c -->|Yes| SV2c1[✓ Enable]
        SV2c -->|No| SV2c2[Skip]

        SV2a1 --> SV3[Save Settings]
        SV2a2 --> SV3
        SV2b1 --> SV3
        SV2b2 --> SV3
        SV2c1 --> SV3
        SV2c2 --> SV3

        SV3 --> SV4[Sales Validation Complete ✓]
    end

    SalesValidation --> CRMConfig

    subgraph CRMConfig[" 📞 STEP 8: CRM Automation "]
        direction TB
        C1[Settings → CRM Settings] --> C2{Configure Automation}

        C2 --> C2a[State After Quotation Creation]
        C2 --> C2b[State After Sale Order Confirmation]

        C2 --> C2c{Auto-Close Leads?}
        C2c -->|Yes| C2c1[✓ Enable<br/>Set Months After Closed<br/>Set Lost Reason]
        C2c -->|No| C2c2[Skip]

        C2a --> C3[Save Settings]
        C2b --> C3
        C2c1 --> C3
        C2c2 --> C3

        C3 --> C4[CRM Config Complete ✓]
    end

    CRMConfig --> Testing

    subgraph Testing[" 🧪 STEP 9: Testing "]
        direction TB
        Test1[Create Test Partner] --> Test2[Test Partner Approval]
        Test2 --> Test3[Create Test Product]
        Test3 --> Test4[Test Product Approval]
        Test4 --> Test5[Create Test Quotation]
        Test5 --> Test6{Test Sales Validations}
        Test6 -->|Enabled| Test6a[Test GP/Credit/Payment]
        Test6 -->|Disabled| Test6b[Skip]
        Test6a --> Test7[Test Email Threading]
        Test6b --> Test7
        Test7 --> Test8[Verify Reports]
        Test8 --> Test9[Testing Complete ✓]
    end

    Testing --> GoLive

    subgraph GoLive[" 🎉 STEP 10: Go Live "]
        direction TB
        GL1[Clean Test Data] --> GL2[Import Production Data]
        GL2 --> GL3[Train Users]
        GL3 --> GL4[Go Live ✓]
    end

    GoLive --> Complete([System Ready for Operations 🚀])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style Complete fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style InstallModules fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style SecuritySetup fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style ApprovalConfig fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style MasterData fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style TaxConfig fill:#558B2F,stroke:#fff,stroke-width:2px,color:#fff
    style SalesValidation fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
    style CRMConfig fill:#5E35B1,stroke:#fff,stroke-width:2px,color:#fff
    style Testing fill:#F57F17,stroke:#fff,stroke-width:2px,color:#fff
    style GoLive fill:#2E7D32,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 📋 Master Data Configuration Flowchart

### Complete Master Data Setup Process

```mermaid
flowchart TB
    Start([Start Master Data Configuration]) --> BusinessNature

    subgraph BusinessNature[" 🏥 Business Nature Setup "]
        direction TB
        BN1[Settings → Lablink Configuration<br/>→ Business Nature] --> BN2[Click Create]
        BN2 --> BN3{Add Entries}

        BN3 --> BN3a[Hospital]
        BN3 --> BN3b[Medical Laboratory]
        BN3 --> BN3c[Research Institute]
        BN3 --> BN3d[University]
        BN3 --> BN3e[Pharmaceutical Company]
        BN3 --> BN3f[Clinical Laboratory]
        BN3 --> BN3g[Diagnostic Center]
        BN3 --> BN3h[Other Custom Entries]

        BN3a --> BN4[Save All Entries]
        BN3b --> BN4
        BN3c --> BN4
        BN3d --> BN4
        BN3e --> BN4
        BN3f --> BN4
        BN3g --> BN4
        BN3h --> BN4

        BN4 --> BN5[Business Nature Complete ✓]
    end

    BusinessNature --> CustomerType

    subgraph CustomerType[" 🏢 Customer Type SSCL Setup "]
        direction TB
        CT1[Settings → Lablink Configuration<br/>→ Customer Type] --> CT2[Click Create]
        CT2 --> CT3[Add Custom Classifications]
        CT3 --> CT4[Save Entries]
        CT4 --> CT5[Customer Type Complete ✓]
    end

    CustomerType --> ProductBrands

    subgraph ProductBrands[" 🏷️ Product Brands Setup "]
        direction TB
        PB1[Inventory → Configuration<br/>→ Brands] --> PB2[Click Create]
        PB2 --> PB3{For Each Brand}

        PB3 --> PB3a[Enter Brand Name]
        PB3a --> PB3b[Upload Brand Logo/Image]
        PB3b --> PB3c[Set Sequence Number]
        PB3c --> PB3d[Save Brand]

        PB3d --> PB4{More Brands?}
        PB4 -->|Yes| PB3
        PB4 -->|No| PB5[Product Brands Complete ✓]
    end

    ProductBrands --> ProductCategories

    subgraph ProductCategories[" 📦 Product Categories Setup "]
        direction TB
        PC1[Inventory → Configuration<br/>→ Product Categories] --> PC2[Select/Create Category]
        PC2 --> PC3{For Each Category}

        PC3 --> PC3a[Enter Category Name<br/>Example: Laboratory Equipment]
        PC3a --> PC3b[Enter Category Code<br/>Example: LAB]
        PC3b --> PC3c[Enter GP Margin %<br/>Example: 15]
        PC3c --> PC3d[Save Category]

        PC3d --> PC4{More Categories?}
        PC4 -->|Yes| PC3
        PC4 -->|No| PC5[Product Categories Complete ✓]

        PC5 --> PC6{Important Categories}
        PC6 --> PC6a[Laboratory Equipment - LAB - 20%]
        PC6 --> PC6b[Consumables - CONS - 15%]
        PC6 --> PC6c[Chemicals - CHEM - 18%]
        PC6 --> PC6d[Glassware - GLASS - 12%]
        PC6 --> PC6e[Instruments - INST - 22%]
    end

    ProductCategories --> Availability

    subgraph Availability[" ⏱️ Availability Options Setup "]
        direction TB
        AV1[Sales → Configuration<br/>→ Availability] --> AV2{Check Pre-configured}

        AV2 --> AV2a[✓ Import & supply within 2-4 weeks]
        AV2 --> AV2b[✓ 4-6 weeks]
        AV2 --> AV2c[✓ 4-8 weeks]
        AV2 --> AV2d[✓ 6-8 weeks]
        AV2 --> AV2e[✓ 8-12 weeks]

        AV2 --> AV3{Add Custom Options?}
        AV3 -->|Yes| AV3a[Click Create]
        AV3a --> AV3b[Enter Availability Description]
        AV3b --> AV3c[Save]
        AV3c --> AV4[Availability Complete ✓]
        AV3 -->|No| AV4
    end

    Availability --> Priority

    subgraph Priority[" ⚡ Sale Order Priority Setup "]
        direction TB
        PR1[Sales → Configuration<br/>→ Sale Order Priority] --> PR2{Check Pre-configured}

        PR2 --> PR2a[✓ Very Urgent - Red Color]
        PR2 --> PR2b[✓ Urgent - Orange Color]
        PR2 --> PR2c[✓ Regular - Gray Color]

        PR2 --> PR3{Add Custom Priorities?}
        PR3 -->|Yes| PR3a[Click Create]
        PR3a --> PR3b[Enter Name]
        PR3b --> PR3c[Set Color]
        PR3c --> PR3d[Set Sequence]
        PR3d --> PR3e[Save]
        PR3e --> PR4[Priority Complete ✓]
        PR3 -->|No| PR4
    end

    Priority --> TaxSetup

    subgraph TaxSetup[" 💰 Tax Types Setup "]
        direction TB
        TX1[Accounting → Configuration<br/>→ Taxes] --> TX2{Create Tax: VAT 18%}

        TX2 --> TX2a[Tax Name: VAT 18%]
        TX2a --> TX2b[Amount: 18.00]
        TX2b --> TX2c[VAT Type: vat]
        TX2c --> TX2d[Tax Type: Sale]
        TX2d --> TX2e[Tax Scope: Goods/Services]
        TX2e --> TX2f[Save]

        TX2f --> TX3{Create Tax: SVAT 8%}

        TX3 --> TX3a[Tax Name: SVAT 8%]
        TX3a --> TX3b[Amount: 8.00]
        TX3b --> TX3c[VAT Type: svat]
        TX3c --> TX3d[Tax Type: Sale]
        TX3d --> TX3e[Tax Scope: Services]
        TX3e --> TX3f[Save]

        TX3f --> TX4{Create Tax: GST}
        TX4 --> TX4a[Configure GST Taxes]
        TX4a --> TX4b[VAT Type: gst]
        TX4b --> TX4c[Save]

        TX4c --> TX5{Create Tax: Other/Non-VAT}
        TX5 --> TX5a[Configure Non-VAT]
        TX5a --> TX5b[VAT Type: other]
        TX5b --> TX5c[Save]

        TX5c --> TX6[Tax Setup Complete ✓]
    end

    TaxSetup --> Complete([Master Data Configuration Complete 🎉])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style Complete fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style BusinessNature fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style CustomerType fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style ProductBrands fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style ProductCategories fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style Availability fill:#558B2F,stroke:#fff,stroke-width:2px,color:#fff
    style Priority fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
    style TaxSetup fill:#5E35B1,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 👥 Partner Management Complete Flowchart

### End-to-End Partner Creation, Approval & Document Management

```mermaid
flowchart TB
    Start([Start: Create New Partner]) --> CreatePartner

    subgraph CreatePartner[" 📝 Partner Creation "]
        direction TB
        CP1[Contacts → Create] --> CP2{Enter Basic Info}

        CP2 --> CP2a[Name]
        CP2 --> CP2b[Company/Individual]
        CP2 --> CP2c[Phone/Mobile/Email]
        CP2 --> CP2d[Address]

        CP2a --> CP3{Enter LabLink Fields}
        CP2b --> CP3
        CP2c --> CP3
        CP2d --> CP3

        CP3 --> CP3a[Customer Type:<br/>Government/Private]
        CP3 --> CP3b[Customer Type SSCL]
        CP3 --> CP3c[Business Nature]
        CP3 --> CP3d[Type of Business]
        CP3 --> CP3e[GRN Type]

        CP3a --> CP4{Enter Sales Config}
        CP3b --> CP4
        CP3c --> CP4
        CP3d --> CP4
        CP3e --> CP4

        CP4 --> CP4a[Quotation Officer]
        CP4 --> CP4b[Commission Rate %]
        CP4 --> CP4c[VAT Type:<br/>VAT/SVAT/Non-VAT/GST]

        CP4a --> CP5{Enter Credit Management}
        CP4b --> CP5
        CP4c --> CP5

        CP5 --> CP5a[Credit Limit]
        CP5 --> CP5b[Payment Terms]

        CP5a --> CP6[Save Partner]
        CP5b --> CP6
    end

    CreatePartner --> DocumentDecision

    subgraph DocumentDecision[" 📄 Document Upload Decision "]
        direction TB
        DD1{Upload Documents Now?} --> DD1a[Yes - Recommended]
        DD1 --> DD1b[No - Upload Later]

        DD1a --> DD2{Upload Documents}
        DD2 --> DD2a[Business Reg Attachments<br/>BR, Incorporation Certificate]
        DD2 --> DD2b[VAT Reg Attachments<br/>VAT Certificate, TIN]
        DD2 --> DD2c[Customer Reg Attachments<br/>Application, Bank Details]

        DD2a --> DD3[Documents Uploaded ✓]
        DD2b --> DD3
        DD2c --> DD3

        DD1b --> DD4[Skip Document Upload]
    end

    DocumentDecision --> ApprovalRequest

    subgraph ApprovalRequest[" ✅ Request Approval "]
        direction TB
        AR1[Click: Request For Approval] --> AR2{Approval Type?}

        AR2 --> AR2a[Single-Level Approval]
        AR2 --> AR2b[Multi-Level Approval]

        AR2a --> AR3a[Select Approvers from Group]
        AR3a --> AR3b[Click: Send Request]

        AR2b --> AR3c[Auto-sends to Level 1 Approvers]

        AR3b --> AR4[Status: Waiting Approval]
        AR3c --> AR4

        AR4 --> AR5[Email Sent to Approvers]
        AR5 --> AR6[Partner Form Locked READ-ONLY]
    end

    ApprovalRequest --> ApprovalProcess

    subgraph ApprovalProcess[" 🔍 Approval Process "]
        direction TB
        AP1{Approval Configuration} --> AP1a[Single Level]
        AP1 --> AP1b[2 Levels]
        AP1 --> AP1c[3 Levels]

        AP1a --> AP2a[Level 1 Reviews]
        AP1b --> AP2b[Level 1 Reviews]
        AP1c --> AP2c[Level 1 Reviews]

        AP2a --> AP3a{Level 1 Decision}
        AP2b --> AP3b{Level 1 Decision}
        AP2c --> AP3c{Level 1 Decision}

        AP3a -->|Approve| AP4a[Status: Approved ✓]
        AP3a -->|Reject| AP5[Status: Draft<br/>Form Editable]

        AP3b -->|Approve| AP6b[Status: First Level Approved]
        AP3b -->|Reject| AP5

        AP3c -->|Approve| AP6c[Status: First Level Approved]
        AP3c -->|Reject| AP5

        AP6b --> AP7b[Auto-escalate to Level 2]
        AP6c --> AP7c[Auto-escalate to Level 2]

        AP7b --> AP8b[Level 2 Reviews]
        AP7c --> AP8c[Level 2 Reviews]

        AP8b --> AP9b{Level 2 Decision}
        AP8c --> AP9c{Level 2 Decision}

        AP9b -->|Approve| AP4b[Status: Approved ✓]
        AP9b -->|Reject| AP5

        AP9c -->|Approve| AP10c[Status: Second Level Approved]
        AP9c -->|Reject| AP5

        AP10c --> AP11c[Auto-escalate to Level 3]
        AP11c --> AP12c[Level 3 Reviews]
        AP12c --> AP13c{Level 3 Decision}

        AP13c -->|Approve| AP4c[Status: Approved ✓]
        AP13c -->|Reject| AP5
    end

    ApprovalProcess --> DocumentCheck

    subgraph DocumentCheck[" 📋 Document Validation "]
        direction TB
        DC1{Final Approval Granted} --> DC2{Documents Uploaded?}

        DC2 -->|Yes| DC3[Status: Approved ✓]
        DC2 -->|No| DC4[Status: Pending Document ⚠️]

        DC4 --> DC5[Start Grace Period Timer<br/>Default: 14 days]

        DC5 --> DC6{Within Grace Period?}

        DC6 -->|Yes, Docs Uploaded| DC7[Click: State For Approved]
        DC7 --> DC3

        DC6 -->|Period Expired| DC8[Auto-change Status:<br/>Approved Without Document ⚠️]

        DC3 --> DC9[Partner Fully Approved ✓<br/>Ready for Business]
    end

    DocumentCheck --> OperationalUse

    subgraph OperationalUse[" 🚀 Operational Use "]
        direction TB
        OU1{Partner Status: Approved} --> OU2[Use in CRM Leads]
        OU1 --> OU3[Create Quotations]
        OU1 --> OU4[Create Sale Orders]
        OU1 --> OU5[Create Invoices]
        OU1 --> OU6[Track Credit Limit]
        OU1 --> OU7[Monitor Payments]

        OU2 --> OU8[Normal Business Operations ✓]
        OU3 --> OU8
        OU4 --> OU8
        OU5 --> OU8
        OU6 --> OU8
        OU7 --> OU8
    end

    OperationalUse --> Monitoring

    subgraph Monitoring[" 📊 Ongoing Monitoring "]
        direction TB
        MN1[Monitor Partner Status] --> MN2{Status Check}

        MN2 --> MN2a{Approved ✓}
        MN2a --> MN3a[All Good - Continue Business]

        MN2 --> MN2b{Pending Document ⚠️}
        MN2b --> MN3b[Upload Documents<br/>Within Grace Period]

        MN2 --> MN2c{Approved Without Doc ⚠️}
        MN2c --> MN3c[Upload Documents Urgently<br/>Contact Admin to Reset]

        MN2 --> MN2d{Suspended ❌}
        MN2d --> MN3d[Investigate & Resolve<br/>Reactivate if Appropriate]
    end

    Monitoring --> Complete([Partner Management Complete 🎉])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style Complete fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style CreatePartner fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style DocumentDecision fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style ApprovalRequest fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style ApprovalProcess fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style DocumentCheck fill:#558B2F,stroke:#fff,stroke-width:2px,color:#fff
    style OperationalUse fill:#2E7D32,stroke:#fff,stroke-width:2px,color:#fff
    style Monitoring fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 📦 Product Management Complete Flowchart

### End-to-End Product Creation, Catalog Upload & Approval

```mermaid
flowchart TB
    Start([Start: Create New Product]) --> CreateProduct

    subgraph CreateProduct[" 📝 Product Creation "]
        direction TB
        PR1[Products → Create] --> PR2{Enter Basic Info}

        PR2 --> PR2a[Product Name]
        PR2 --> PR2b[Can be Sold ✓]
        PR2 --> PR2c[Can be Purchased]
        PR2 --> PR2d[Product Type:<br/>Storable/Consumable/Service]

        PR2a --> PR3{Select Category}
        PR2b --> PR3
        PR2c --> PR3
        PR2d --> PR3

        PR3 --> PR3a[Select Product Category<br/>Example: Laboratory Equipment]
        PR3a --> PR3b[Category Code Auto-Shown<br/>Example: LAB]

        PR3b --> PR4{Enter Product Identification}

        PR4 --> PR4a[Product Code<br/>Example: LB-CENT-5000]
        PR4 --> PR4b[Internal Reference:<br/>AUTO-GENERATED<br/>LAB-LB-CENT-5000]

        PR4a --> PR5{Enter Product Details}
        PR4b --> PR5

        PR5 --> PR5a[Brand<br/>Select from Brand Master]
        PR5 --> PR5b[Country of Origin]
        PR5 --> PR5c[Warranty Period<br/>Example: 24 months]

        PR5a --> PR6{Enter Pricing}
        PR5b --> PR6
        PR5c --> PR6

        PR6 --> PR6a[Sales Price<br/>Example: LKR 250,000]
        PR6 --> PR6b[Cost<br/>Example: LKR 180,000]
        PR6 --> PR6c[GP Margin %<br/>AUTO-CALCULATED<br/>28%]

        PR6a --> PR7[Save Product]
        PR6b --> PR7
        PR6c --> PR7
    end

    CreateProduct --> CatalogUpload

    subgraph CatalogUpload[" 📄 Product Catalog Upload (MANDATORY) "]
        direction TB
        CU1[Scroll to: Product Catalogs Section] --> CU2[Click: Upload/Add a file]

        CU2 --> CU3{Upload Files}

        CU3 --> CU3a[Product Brochure PDF]
        CU3 --> CU3b[Technical Specifications PDF/DOCX]
        CU3 --> CU3c[Datasheet]
        CU3 --> CU3d[User Manual]
        CU3 --> CU3e[Certificates]
        CU3 --> CU3f[Images]

        CU3a --> CU4[Multiple Files Attached ✓]
        CU3b --> CU4
        CU3c --> CU4
        CU3d --> CU4
        CU3e --> CU4
        CU3f --> CU4

        CU4 --> CU5[Save Product]
        CU5 --> CU6[Catalog Upload Complete ✓]
    end

    CatalogUpload --> ValidationCheck

    subgraph ValidationCheck[" ✅ Pre-Approval Validation "]
        direction TB
        VC1[Click: Request For Approval] --> VC2{Validation Check}

        VC2 --> VC3{Product Catalogs Uploaded?}

        VC3 -->|No| VC4[❌ ERROR MESSAGE<br/>Please upload product catalogs<br/>before requesting approval]
        VC4 --> VC5[Return to Product Form]
        VC5 --> VC6[Upload Catalogs]
        VC6 --> VC1

        VC3 -->|Yes| VC7{All Required Fields Complete?}

        VC7 -->|No| VC8[❌ ERROR MESSAGE<br/>Complete all required fields]
        VC8 --> VC5

        VC7 -->|Yes| VC9[✓ Validation Passed<br/>Proceed to Approval]
    end

    ValidationCheck --> ApprovalRequest

    subgraph ApprovalRequest[" 📨 Approval Request "]
        direction TB
        AR1[Select Approvers] --> AR2[Approvers from:<br/>Approve/Reject Product Group]
        AR2 --> AR3[Click: Send Request]

        AR3 --> AR4[Status: Waiting Approval]
        AR4 --> AR5[Email Sent to Approvers]
        AR5 --> AR6[Product Form: READ-ONLY 🔒]

        AR6 --> AR7{Product Cannot Be Modified<br/>During Approval}
    end

    ApprovalRequest --> ApprovalProcess

    subgraph ApprovalProcess[" 🔍 Approver Reviews Product "]
        direction TB
        AP1[Approver Opens Product] --> AP2{Review Checklist}

        AP2 --> AP2a{Product Name Descriptive?}
        AP2a -->|No| AP3[REJECT]
        AP2a -->|Yes| AP2b{Category/Brand Correct?}

        AP2b -->|No| AP3
        AP2b -->|Yes| AP2c{Pricing Reasonable?}

        AP2c -->|No| AP3
        AP2c -->|Yes| AP2d{GP Margin Acceptable?}

        AP2d -->|No| AP3
        AP2d -->|Yes| AP2e{Product Catalogs Present?}

        AP2e -->|No| AP3
        AP2e -->|Yes| AP2f{All Details Complete?}

        AP2f -->|No| AP3
        AP2f -->|Yes| AP4[APPROVE ✓]

        AP3 --> AP5[Click: Reject Button]
        AP5 --> AP6[Enter Rejection Reason:<br/>- Incomplete specifications<br/>- Incorrect pricing<br/>- Missing catalogs<br/>- Classification error]
        AP6 --> AP7[Click: Reject]

        AP7 --> AP8[Status: Draft]
        AP8 --> AP9[Form Editable Again]
        AP9 --> AP10[Email Sent to Requestor]

        AP4 --> AP11[Click: Approve Button]
        AP11 --> AP12[Enter Approval Notes Optional]
        AP12 --> AP13[Click: Approve]

        AP13 --> AP14[Status: Approved ✓]
        AP14 --> AP15[Form Locked READ-ONLY 🔒]
        AP15 --> AP16[Email Sent to Requestor]
    end

    ApprovalProcess --> TransactionAvailability

    subgraph TransactionAvailability[" 🚀 Product in Transactions "]
        direction TB
        TA1{Product Status} --> TA2{Draft/Waiting/Rejected}
        TA1 --> TA3{Approved ✓}

        TA2 --> TA4[❌ BLOCKED from:]
        TA4 --> TA4a[Sales Orders]
        TA4 --> TA4b[Purchase Orders]
        TA4 --> TA4c[Invoices]
        TA4 --> TA4d[Stock Moves]

        TA4a --> TA5[Error Message:<br/>Product must be approved]
        TA4b --> TA5
        TA4c --> TA5
        TA4d --> TA5

        TA3 --> TA6[✓ AVAILABLE in:]
        TA6 --> TA6a[Sales Orders ✓]
        TA6 --> TA6b[Purchase Orders ✓]
        TA6 --> TA6c[Invoices ✓]
        TA6 --> TA6d[Stock Moves ✓]
        TA6 --> TA6e[Quotations ✓]

        TA6a --> TA7[Product Ready for Business ✓]
        TA6b --> TA7
        TA6c --> TA7
        TA6d --> TA7
        TA6e --> TA7
    end

    TransactionAvailability --> SalesOrderLine

    subgraph SalesOrderLine[" 💼 Product in Sale Order Line "]
        direction TB
        SO1[Add Product to Sale Order] --> SO2{Auto-Populated Fields}

        SO2 --> SO2a[Sequence: 1, 2, 3...]
        SO2 --> SO2b[Internal Reference: LAB-LB-CENT-5000]
        SO2 --> SO2c[Brand: Thermo Fisher]
        SO2 --> SO2d[Country of Origin: Germany]
        SO2 --> SO2e[Warranty: 24 months]

        SO2a --> SO3{Price History Shows}
        SO2b --> SO3
        SO2c --> SO3
        SO2d --> SO3
        SO2e --> SO3

        SO3 --> SO3a[Last Quoted Price:<br/>LKR 240,000]
        SO3 --> SO3b[Last Invoiced Price:<br/>LKR 245,000]

        SO3a --> SO4[Helps Maintain<br/>Pricing Consistency ✓]
        SO3b --> SO4
    end

    SalesOrderLine --> Complete([Product Management Complete 🎉])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style Complete fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style CreateProduct fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style CatalogUpload fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
    style ValidationCheck fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style ApprovalRequest fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style ApprovalProcess fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style TransactionAvailability fill:#558B2F,stroke:#fff,stroke-width:2px,color:#fff
    style SalesOrderLine fill:#2E7D32,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 📞 CRM to Sales Complete Flowchart

### Lead Creation → Quotation → Order with Email Threading

```mermaid
flowchart TB
    Start([Start: Customer Inquiry]) --> CreateLead

    subgraph CreateLead[" 📋 CRM Lead Creation "]
        direction TB
        CL1[CRM → My Pipeline → Create] --> CL2{Enter Lead Info}

        CL2 --> CL2a[Opportunity Name]
        CL2 --> CL2b[Customer: Select/Create]
        CL2 --> CL2c[Email]
        CL2 --> CL2d[Phone]
        CL2 --> CL2e[Expected Revenue]
        CL2 --> CL2f[Probability %]

        CL2a --> CL3{Auto-Fill Fields}
        CL2b --> CL3
        CL2c --> CL3
        CL2d --> CL3
        CL2e --> CL3
        CL2f --> CL3

        CL3 --> CL3a[Salesperson:<br/>AUTO from Customer's<br/>Quotation Officer ✓]
        CL3 --> CL3b[Sales Team:<br/>From Salesperson]

        CL3a --> CL4[Save Lead]
        CL3b --> CL4

        CL4 --> CL5[Stage: New]
        CL5 --> CL6[System Generates:<br/>UUID for Email Threading]
    end

    CreateLead --> FirstEmail

    subgraph FirstEmail[" 📧 First Email from Lead (Important for Threading) "]
        direction TB
        FE1[Open Lead] --> FE2[Click: Send Message/Email]
        FE2 --> FE3[Compose Email]

        FE3 --> FE3a[To: Customer Email]
        FE3 --> FE3b[Subject: Equipment Inquiry]
        FE3 --> FE3c[Body: Initial Contact]

        FE3a --> FE4[Click: Send]
        FE3b --> FE4
        FE3c --> FE4

        FE4 --> FE5{System Captures}

        FE5 --> FE5a[email_thread_message_id:<br/>Message-ID Header]
        FE5 --> FE5b[email_thread_subject:<br/>Equipment Inquiry]

        FE5a --> FE6[Email Thread Info Saved ✓]
        FE5b --> FE6
    end

    FirstEmail --> CreateQuotation

    subgraph CreateQuotation[" 💰 Create Quotation from Lead "]
        direction TB
        CQ1[Open Lead] --> CQ2[Click: New Quotation Button]

        CQ2 --> CQ3{Auto-Populated from Lead}

        CQ3 --> CQ3a[Customer]
        CQ3 --> CQ3b[Opportunity: Linked to Lead]
        CQ3 --> CQ3c[Email Thread Info:<br/>INHERITED ✓]

        CQ3a --> CQ4{Auto-Populated from Customer}
        CQ3b --> CQ4
        CQ3c --> CQ4

        CQ4 --> CQ4a[Customer Type]
        CQ4 --> CQ4b[Customer Type SSCL]
        CQ4 --> CQ4c[Quotation Officer]
        CQ4 --> CQ4d[Commission Rate %]
        CQ4 --> CQ4e[VAT Type]

        CQ4a --> CQ5{Enter Quotation Details}
        CQ4b --> CQ5
        CQ4c --> CQ5
        CQ4d --> CQ5
        CQ4e --> CQ5

        CQ5 --> CQ5a[Quotation Type]
        CQ5 --> CQ5b[Quotation Heading]
        CQ5 --> CQ5c[Contact Person]
        CQ5 --> CQ5d[Priority Level]
        CQ5 --> CQ5e[Inquiry Date]
        CQ5 --> CQ5f[PO Number if available]
    end

    CreateQuotation --> AddProducts

    subgraph AddProducts[" 📦 Add Products to Quotation "]
        direction TB
        AP1[Add Product Line] --> AP2{Select APPROVED Product}

        AP2 --> AP2a[Product Dropdown:<br/>Shows ONLY Approved Products ✓]

        AP2a --> AP3{Auto-Populated}

        AP3 --> AP3a[Sequence: 1]
        AP3 --> AP3b[Internal Reference]
        AP3 --> AP3c[Brand]
        AP3 --> AP3d[Country of Origin]
        AP3 --> AP3e[Warranty Period]

        AP3a --> AP4{Price History Shown}
        AP3b --> AP4
        AP3c --> AP4
        AP3d --> AP4
        AP3e --> AP4

        AP4 --> AP4a[Last Quoted Price:<br/>Helps set current price]
        AP4 --> AP4b[Last Invoiced Price:<br/>Reference for pricing]

        AP4a --> AP5{Enter Line Details}
        AP4b --> AP5

        AP5 --> AP5a[Quantity]
        AP5 --> AP5b[Unit Price]
        AP5 --> AP5c[Discount %]
        AP5 --> AP5d[Availability:<br/>Select lead time]
        AP5 --> AP5e[Taxes: AUTO Applied<br/>based on VAT Type]

        AP5a --> AP6{More Products?}
        AP5b --> AP6
        AP5c --> AP6
        AP5d --> AP6
        AP5e --> AP6

        AP6 -->|Yes| AP1
        AP6 -->|No| AP7[Review Order Totals]

        AP7 --> AP7a[Untaxed Amount]
        AP7 --> AP7b[Tax Amount]
        AP7 --> AP7c[SVAT if Government]
        AP7 --> AP7d[Total]

        AP7a --> AP8[Save Quotation]
        AP7b --> AP8
        AP7c --> AP8
        AP7d --> AP8
    end

    AddProducts --> SendQuotation

    subgraph SendQuotation[" 📨 Send Quotation Email "]
        direction TB
        SQ1[Click: Send by Email] --> SQ2{Email Compose Window}

        SQ2 --> SQ2a[To: Customer Email AUTO]
        SQ2 --> SQ2b[Subject:<br/>Re: Equipment Inquiry<br/>CONTINUES THREAD ✓]
        SQ2 --> SQ2c[Body: Email Template]
        SQ2 --> SQ2d[Attachment: Quotation PDF AUTO]

        SQ2a --> SQ3{Email Headers Set}
        SQ2b --> SQ3
        SQ2c --> SQ3
        SQ2d --> SQ3

        SQ3 --> SQ3a[Message-ID: SAME as Lead]
        SQ3 --> SQ3b[In-Reply-To: Lead Message-ID]
        SQ3 --> SQ3c[References: Lead Message-ID]

        SQ3a --> SQ4[Click: Send]
        SQ3b --> SQ4
        SQ3c --> SQ4

        SQ4 --> SQ5[Email Sent ✓]
        SQ5 --> SQ6[Customer Sees in SAME Thread ✓]
    end

    SendQuotation --> CRMStageUpdate1

    subgraph CRMStageUpdate1[" 🔄 CRM Auto-Stage Update (Quotation) "]
        direction TB
        CS1[Quotation Created] --> CS2[Trigger: Update CRM Stage]

        CS2 --> CS3[Read Configuration:<br/>State After Quotation Creation]

        CS3 --> CS4[Example: Quotation Sent]

        CS4 --> CS5[Lead Stage AUTO Updated ✓]
        CS5 --> CS6[Stage: Quotation Sent]

        CS6 --> CS7[Chatter Message Posted:<br/>Quotation Created]
    end

    CRMStageUpdate1 --> CustomerResponse

    subgraph CustomerResponse[" 💬 Customer Response & Follow-up "]
        direction TB
        CR1[Wait for Customer Response] --> CR2{Customer Action}

        CR2 --> CR2a[Accepts & Sends PO]
        CR2 --> CR2b[Requests Changes]
        CR2 --> CR2c[No Response]

        CR2a --> CR3a[Update PO Number in Quotation]
        CR3a --> CR3b[Update PO Received Date]

        CR2b --> CR4b[Modify Quotation]
        CR4b --> CR4c[Send Updated Quotation]
        CR4c --> CR4d[Email CONTINUES Same Thread ✓]

        CR2c --> CR5c{Auto-Close Enabled?}
        CR5c -->|Yes| CR6c[After X Months:<br/>Cron Auto-Closes as Lost]
        CR5c -->|No| CR7c[Manual Follow-up]
    end

    CustomerResponse --> ConfirmOrder

    subgraph ConfirmOrder[" ✅ Confirm Sale Order "]
        direction TB
        CO1[Click: Confirm Button] --> CO2{Sales Validations Enabled?}

        CO2 -->|No| CO3[Order Confirmed Immediately ✓]

        CO2 -->|Yes| CO4{Run Validation Checks}

        CO4 --> CO4a{GP Margin Check}
        CO4 --> CO4b{Credit Limit Check}
        CO4 --> CO4c{Payment Terms Check}

        CO4a -->|FAIL| CO5[Status: Pending]
        CO4b -->|FAIL| CO5
        CO4c -->|FAIL| CO5

        CO4a -->|PASS| CO6{All Pass?}
        CO4b -->|PASS| CO6
        CO4c -->|PASS| CO6

        CO6 -->|Yes| CO3
        CO6 -->|No| CO5

        CO5 --> CO7[Send for Approval]
        CO7 --> CO8[Approver Approves]
        CO8 --> CO9[Status: Approved]
        CO9 --> CO10[Click Confirm Again]
        CO10 --> CO3
    end

    ConfirmOrder --> CRMStageUpdate2

    subgraph CRMStageUpdate2[" 🔄 CRM Auto-Stage Update (Order) "]
        direction TB
        CS21[Order Confirmed] --> CS22[Trigger: Update CRM Stage]

        CS22 --> CS23[Read Configuration:<br/>State After Sale Order Confirmation]

        CS23 --> CS24[Example: Won]

        CS24 --> CS25[Lead Stage AUTO Updated ✓]
        CS25 --> CS26[Stage: Won]
        CS26 --> CS27[Lead Status: Won ✓]

        CS27 --> CS28[Chatter Message Posted:<br/>Order Confirmed - Lead Won]
    end

    CRMStageUpdate2 --> OrderProcessing

    subgraph OrderProcessing[" 📦 Order Processing "]
        direction TB
        OP1[Order Confirmed] --> OP2{Auto-Created}

        OP2 --> OP2a[Delivery Order<br/>if Storable Products]
        OP2 --> OP2b[Manufacturing Order<br/>if Kit/BoM Products]

        OP2a --> OP3[Process Delivery]
        OP2b --> OP3

        OP3 --> OP4[Click: Create Invoice]

        OP4 --> OP5{Invoice Inherits}

        OP5 --> OP5a[Customer Details]
        OP5 --> OP5b[Order Lines + Sequences]
        OP5 --> OP5c[VAT Type]
        OP5 --> OP5d[Email Thread Info ✓]
        OP5 --> OP5e[Approval Tracking:<br/>approved_by, credit_approved_by,<br/>pt_approved_by]

        OP5a --> OP6[Confirm Invoice]
        OP5b --> OP6
        OP5c --> OP6
        OP5d --> OP6
        OP5e --> OP6
    end

    OrderProcessing --> SendInvoice

    subgraph SendInvoice[" 📧 Send Invoice Email "]
        direction TB
        SI1[Click: Send & Print] --> SI2{Email Compose}

        SI2 --> SI2a[To: Customer Email]
        SI2 --> SI2b[Subject:<br/>Re: Equipment Inquiry<br/>SAME THREAD ✓]
        SI2 --> SI2c[Attachment: Invoice PDF]

        SI2a --> SI3{Email Headers}
        SI2b --> SI3
        SI2c --> SI3

        SI3 --> SI3a[Message-ID: SAME UUID]
        SI3 --> SI3b[In-Reply-To: Original]
        SI3 --> SI3c[References: Original]

        SI3a --> SI4[Click: Send]
        SI3b --> SI4
        SI3c --> SI4

        SI4 --> SI5[Invoice Email Sent ✓]
        SI5 --> SI6[Customer Inbox:<br/>ONE Conversation Thread ✓]

        SI6 --> SI7{Customer Sees}
        SI7 --> SI7a[📧 Initial Inquiry Lead]
        SI7 --> SI7b[📧 Quotation Email]
        SI7 --> SI7c[📧 Order Confirmation]
        SI7 --> SI7d[📧 Invoice]

        SI7a --> SI8[All in SINGLE Thread ✓]
        SI7b --> SI8
        SI7c --> SI8
        SI7d --> SI8
    end

    SendInvoice --> Complete([Complete Sales Cycle 🎉])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style Complete fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style CreateLead fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style FirstEmail fill:#5E35B1,stroke:#fff,stroke-width:2px,color:#fff
    style CreateQuotation fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style AddProducts fill:#558B2F,stroke:#fff,stroke-width:2px,color:#fff
    style SendQuotation fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style CRMStageUpdate1 fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style ConfirmOrder fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
    style CRMStageUpdate2 fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style OrderProcessing fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style SendInvoice fill:#2E7D32,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 🔍 Sales Order Validation Complete Flowchart

### GP Margin + Credit Limit + Payment Terms Validation

```mermaid
flowchart TB
    Start([User Clicks: Confirm on Quotation]) --> CheckEnabled

    subgraph CheckEnabled[" ⚙️ Check What's Enabled "]
        direction TB
        CE1{Settings → Sales<br/>Validations Enabled?} --> CE2{GP Margin}
        CE1 --> CE3{Credit Limit}
        CE1 --> CE4{Payment Terms}

        CE2 -->|Enabled ✓| CE2a[Will Check GP]
        CE2 -->|Disabled| CE2b[Skip GP Check]

        CE3 -->|Enabled ✓| CE3a[Will Check Credit]
        CE3 -->|Disabled| CE3b[Skip Credit Check]

        CE4 -->|Enabled ✓| CE4a[Will Check Payment]
        CE4 -->|Disabled| CE4b[Skip Payment Check]
    end

    CheckEnabled --> GPMarginValidation

    subgraph GPMarginValidation[" 💰 GP Margin Validation "]
        direction TB
        GP1{GP Margin Enabled?} -->|No| GP2[Skip GP Validation]

        GP1 -->|Yes| GP3[For Each Order Line]

        GP3 --> GP4{Calculate Margin %}
        GP4 --> GP4a[Formula:<br/>line_margin_pct =<br/>price_unit - product.standard_price<br/>/ price_unit × 100]

        GP4a --> GP5{Get Minimum Margin}

        GP5 --> GP5a[Check Product Category GP Margin]
        GP5 --> GP5b[Check Company GP Margin]

        GP5a --> GP6{Which to Use?}
        GP5b --> GP6

        GP6 --> GP6a[If Category has GP Margin:<br/>Use Category GP Margin]
        GP6 --> GP6b[Else:<br/>Use Company GP Margin]

        GP6a --> GP7{Compare}
        GP6b --> GP7

        GP7 --> GP8{line_margin_pct < min_margin?}

        GP8 -->|Yes| GP9[❌ GP VALIDATION TRIGGERED]
        GP9 --> GP10[triggered_gp_margin_validation = True]

        GP8 -->|No| GP11[✓ GP VALIDATION PASSED]
    end

    GPMarginValidation --> CreditLimitValidation

    subgraph CreditLimitValidation[" 💳 Credit Limit Validation "]
        direction TB
        CL1{Credit Limit Enabled?} -->|No| CL2[Skip Credit Validation]

        CL1 -->|Yes| CL3[Get Customer Credit Limit]

        CL3 --> CL4[Get Total Unpaid Invoices]
        CL4 --> CL5[Get Current Order Total]

        CL5 --> CL6{Calculate Remaining}

        CL6 --> CL6a[Formula:<br/>remaining_credit_limit =<br/>partner.credit_limit -<br/>partner.total_receivable -<br/>order.amount_total]

        CL6a --> CL7{remaining_credit_limit < 0?}

        CL7 -->|Yes| CL8[❌ CREDIT LIMIT TRIGGERED]
        CL8 --> CL9[triggered_credit_limit_validation = True]

        CL7 -->|No| CL10[✓ CREDIT VALIDATION PASSED]
    end

    CreditLimitValidation --> PaymentTermsValidation

    subgraph PaymentTermsValidation[" 📅 Payment Terms Validation "]
        direction TB
        PT1{Payment Terms Enabled?} -->|No| PT2[Skip Payment Validation]

        PT1 -->|Yes| PT3[Get Customer Invoices]

        PT3 --> PT4[Filter: Posted & Unpaid]

        PT4 --> PT5{Check Each Invoice}

        PT5 --> PT5a{invoice.date_due < today?}

        PT5a -->|Yes for ANY| PT6[❌ PAYMENT TERMS TRIGGERED]
        PT6 --> PT7[triggered_payment_term_validation = True]

        PT5a -->|No for ALL| PT8[✓ PAYMENT VALIDATION PASSED]

        PT6 --> PT9[Calculate Pending Credit Days]
        PT9 --> PT9a[Find Oldest Overdue Invoice]
        PT9a --> PT9b[pending_credit_days =<br/>today - oldest.date_due]
    end

    PaymentTermsValidation --> ValidationResults

    subgraph ValidationResults[" 📊 Validation Results "]
        direction TB
        VR1{Any Validation Triggered?} --> VR2{Check Results}

        VR2 --> VR2a{GP Triggered?}
        VR2 --> VR2b{Credit Triggered?}
        VR2 --> VR2c{Payment Triggered?}

        VR2a -->|No| VR3a[GP: PASS ✓]
        VR2a -->|Yes| VR4a[GP: FAIL ❌]

        VR2b -->|No| VR3b[Credit: PASS ✓]
        VR2b -->|Yes| VR4b[Credit: FAIL ❌]

        VR2c -->|No| VR3c[Payment: PASS ✓]
        VR2c -->|Yes| VR4c[Payment: FAIL ❌]

        VR3a --> VR5{All Passed?}
        VR3b --> VR5
        VR3c --> VR5

        VR4a --> VR6[At Least One Failed]
        VR4b --> VR6
        VR4c --> VR6

        VR5 -->|Yes| VR7[Confirm Order Immediately ✓]
        VR5 -->|No| VR6

        VR6 --> VR8[Status: Pending ⚠️]
    end

    ValidationResults --> ApprovalRequired

    subgraph ApprovalRequired[" 📧 Send for Approval "]
        direction TB
        AR1[Status: Pending] --> AR2{User's Options}

        AR2 --> AR3{Separate Approvals}
        AR2 --> AR4{Combined Approval}

        AR3 --> AR3a{GP Triggered?}
        AR3a -->|Yes| AR3a1[Click:<br/>Send for GP Margin Approval]
        AR3a1 --> AR3a2[Select Approvers from:<br/>Sales Order Gross Profit Approver]

        AR3 --> AR3b{Credit Triggered?}
        AR3b -->|Yes| AR3b1[Click:<br/>Send for Credit Limit Approval]
        AR3b1 --> AR3b2[Select Approvers from:<br/>Sales Order Credit Limit Approver]

        AR3 --> AR3c{Payment Triggered?}
        AR3c -->|Yes| AR3c1[Click:<br/>Send for Payment Term Approval]
        AR3c1 --> AR3c2[Select Approvers from:<br/>Sales Order Payment Term Approver]

        AR4 --> AR4a[Click:<br/>Send for All Validations Approval]
        AR4a --> AR4b[Select Approvers from:<br/>Sales Order All Validations Approver]

        AR3a2 --> AR5[Email Sent to Approvers]
        AR3b2 --> AR5
        AR3c2 --> AR5
        AR4b --> AR5
    end

    ApprovalRequired --> ApproverReview

    subgraph ApproverReview[" 🔍 Approver Reviews Order "]
        direction TB
        AV1[Approver Opens Order] --> AV2{Review Type}

        AV2 --> AV3a{GP Margin Review}
        AV3a --> AV3a1[Check Margin % on Lines]
        AV3a1 --> AV3a2[Compare vs Threshold]
        AV3a2 --> AV3a3{Acceptable?}

        AV3a3 -->|Yes| AV3a4[Click: Approve GP Margin]
        AV3a3 -->|No| AV3a5[Click: Reject]

        AV3a4 --> AV3a6[approved_by = Current User]

        AV2 --> AV3b{Credit Limit Review}
        AV3b --> AV3b1[Check Remaining Credit Limit]
        AV3b1 --> AV3b2[Review Customer Payment History]
        AV3b2 --> AV3b3{Accept Risk?}

        AV3b3 -->|Yes| AV3b4[Click: Approve Credit Limit]
        AV3b3 -->|No| AV3b5[Click: Reject]

        AV3b4 --> AV3b6[credit_approved_by = Current User]

        AV2 --> AV3c{Payment Terms Review}
        AV3c --> AV3c1[Check Pending Credit Days]
        AV3c1 --> AV3c2[Review Overdue Invoices]
        AV3c2 --> AV3c3{Acceptable?}

        AV3c3 -->|Yes| AV3c4[Click: Approve Payment Term]
        AV3c3 -->|No| AV3c5[Click: Reject]

        AV3c4 --> AV3c6[pt_approved_by = Current User]

        AV3a5 --> AV4[Status: Quotation]
        AV3b5 --> AV4
        AV3c5 --> AV4

        AV4 --> AV5[User Can Modify Order]
        AV5 --> AV6[Resubmit After Changes]

        AV3a6 --> AV7{All Required Approvals Done?}
        AV3b6 --> AV7
        AV3c6 --> AV7

        AV7 -->|Yes| AV8[Status: Approved ✓]
        AV7 -->|No| AV9[Wait for Other Approvals]
    end

    ApproverReview --> FinalConfirmation

    subgraph FinalConfirmation[" ✅ Final Confirmation "]
        direction TB
        FC1[Status: Approved] --> FC2[User Clicks: Confirm Again]

        FC2 --> FC3[Order Confirmed ✓]

        FC3 --> FC4{Auto-Created}

        FC4 --> FC4a[Delivery Order<br/>if applicable]
        FC4 --> FC4b[Status: Sale Order]

        FC4a --> FC5[Order Processing Begins]
        FC4b --> FC5

        FC5 --> FC6{Approval Tracking Maintained}

        FC6 --> FC6a[approved_by: Stored]
        FC6 --> FC6b[credit_approved_by: Stored]
        FC6 --> FC6c[pt_approved_by: Stored]

        FC6a --> FC7[Full Audit Trail ✓]
        FC6b --> FC7
        FC6c --> FC7
    end

    FinalConfirmation --> InvoiceInheritance

    subgraph InvoiceInheritance[" 📄 Invoice Inherits Approval Data "]
        direction TB
        II1[Create Invoice from Order] --> II2{Invoice Inherits}

        II2 --> II2a[approved_by<br/>GP Margin Approver]
        II2 --> II2b[credit_approved_by<br/>Credit Limit Approver]
        II2 --> II2c[pt_approved_by<br/>Payment Term Approver]

        II2a --> II3[Complete Approval History<br/>Visible on Invoice ✓]
        II2b --> II3
        II2c --> II3
    end

    InvoiceInheritance --> Complete([Sales Validation Complete 🎉])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style Complete fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style CheckEnabled fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style GPMarginValidation fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style CreditLimitValidation fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
    style PaymentTermsValidation fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style ValidationResults fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style ApprovalRequired fill:#558B2F,stroke:#fff,stroke-width:2px,color:#fff
    style ApproverReview fill:#5E35B1,stroke:#fff,stroke-width:2px,color:#fff
    style FinalConfirmation fill:#2E7D32,stroke:#fff,stroke-width:2px,color:#fff
    style InvoiceInheritance fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 🏢 Complete Business Process Flowchart

### Full End-to-End Business Flow

```mermaid
flowchart TB
    Start([Business Day Starts]) --> SystemReady

    subgraph SystemReady[" ✅ Prerequisites Check "]
        direction TB
        SR1{System Configured?} --> SR2{Master Data Ready?}
        SR2 --> SR3{Users Trained?}

        SR1 -->|No| SR1a[Complete Initial Setup]
        SR1 -->|Yes| SR2

        SR2 -->|No| SR2a[Setup Master Data]
        SR2 -->|Yes| SR3

        SR3 -->|No| SR3a[Train Users]
        SR3 -->|Yes| SR4[System Ready ✓]
    end

    SystemReady --> MasterDataOps

    subgraph MasterDataOps[" 📋 Master Data Operations "]
        direction TB
        MD1{New Partners?} -->|Yes| MD1a[Create Partner]
        MD1a --> MD1b[Upload Documents]
        MD1b --> MD1c[Request Approval]
        MD1c --> MD1d[Approver Approves]
        MD1d --> MD1e[Partner: Approved ✓]

        MD1 -->|No| MD2{New Products?}

        MD2 -->|Yes| MD2a[Create Product]
        MD2a --> MD2b[Upload Catalogs]
        MD2b --> MD2c[Request Approval]
        MD2c --> MD2d[Approver Approves]
        MD2d --> MD2e[Product: Approved ✓]

        MD2 -->|No| MD3[Master Data Ready]
        MD1e --> MD3
        MD2e --> MD3
    end

    MasterDataOps --> CustomerInquiry

    subgraph CustomerInquiry[" 📞 Customer Inquiry "]
        direction TB
        CI1[Customer Contacts] --> CI2{Inquiry Channel}

        CI2 --> CI2a[Phone Call]
        CI2 --> CI2b[Email]
        CI2 --> CI2c[Walk-in]
        CI2 --> CI2d[Website Form]

        CI2a --> CI3[Create CRM Lead]
        CI2b --> CI3
        CI2c --> CI3
        CI2d --> CI3

        CI3 --> CI4{Fill Lead Details}
        CI4 --> CI4a[Customer:<br/>Select Approved Partner]
        CI4 --> CI4b[Expected Revenue]
        CI4 --> CI4c[Probability]
        CI4 --> CI4d[Salesperson:<br/>AUTO from Customer ✓]

        CI4a --> CI5[Save Lead]
        CI4b --> CI5
        CI4c --> CI5
        CI4d --> CI5

        CI5 --> CI6[Send Initial Email]
        CI6 --> CI7[Email Thread Created ✓]
    end

    CustomerInquiry --> QuotationPrep

    subgraph QuotationPrep[" 💰 Quotation Preparation "]
        direction TB
        QP1[Open Lead] --> QP2[Click: New Quotation]

        QP2 --> QP3{Auto-Populated}
        QP3 --> QP3a[Customer Details]
        QP3 --> QP3b[Quotation Officer]
        QP3 --> QP3c[Commission Rate]
        QP3 --> QP3d[VAT Type]
        QP3 --> QP3e[Email Thread Info ✓]

        QP3a --> QP4{Enter Quotation Details}
        QP3b --> QP4
        QP3c --> QP4
        QP3d --> QP4
        QP3e --> QP4

        QP4 --> QP4a[Priority Level]
        QP4 --> QP4b[Quotation Type]
        QP4 --> QP4c[Quotation Heading]
        QP4 --> QP4d[Contact Person]

        QP4a --> QP5{Add Products}
        QP4b --> QP5
        QP4c --> QP5
        QP4d --> QP5

        QP5 --> QP5a[Select APPROVED Products Only]
        QP5a --> QP5b[View Price History]
        QP5b --> QP5c[Enter Quantity & Price]
        QP5c --> QP5d[Select Availability]
        QP5d --> QP5e[Taxes AUTO Applied]

        QP5e --> QP6[Save Quotation]
        QP6 --> QP7[Send Email:<br/>Same Thread ✓]
    end

    QuotationPrep --> CRMUpdate1

    subgraph CRMUpdate1[" 🔄 CRM Stage Auto-Update "]
        direction TB
        CU1[Quotation Created] --> CU2[Trigger: Auto-Update]
        CU2 --> CU3[Lead Stage → Quotation Sent ✓]
    end

    CRMUpdate1 --> CustomerDecision

    subgraph CustomerDecision[" 🤔 Customer Decision "]
        direction TB
        CD1[Customer Reviews Quotation] --> CD2{Customer Decision}

        CD2 --> CD2a[Accepts<br/>Sends PO]
        CD2 --> CD2b[Requests Changes]
        CD2 --> CD2c[Rejects/No Response]

        CD2a --> CD3a[Update PO Number]
        CD3a --> CD3b[Proceed to Confirm]

        CD2b --> CD4b[Modify Quotation]
        CD4b --> CD4c[Send Updated Quote<br/>Same Thread ✓]
        CD4c --> CD1

        CD2c --> CD5c{Auto-Close Enabled?}
        CD5c -->|Yes| CD6c[After X Months:<br/>Auto-Close as Lost]
        CD5c -->|No| CD7c[Mark Lost Manually]
    end

    CustomerDecision --> OrderConfirmation

    subgraph OrderConfirmation[" ✅ Order Confirmation "]
        direction TB
        OC1[Click: Confirm] --> OC2{Validations Enabled?}

        OC2 -->|No| OC3[Confirm Immediately ✓]

        OC2 -->|Yes| OC4{Run Validations}

        OC4 --> OC4a{GP Margin?}
        OC4 --> OC4b{Credit Limit?}
        OC4 --> OC4c{Payment Terms?}

        OC4a -->|PASS| OC5{All Pass?}
        OC4b -->|PASS| OC5
        OC4c -->|PASS| OC5

        OC5 -->|Yes| OC3

        OC4a -->|FAIL| OC6[Status: Pending]
        OC4b -->|FAIL| OC6
        OC4c -->|FAIL| OC6

        OC6 --> OC7[Send for Approval]
        OC7 --> OC8[Approver Reviews & Approves]
        OC8 --> OC9[Status: Approved]
        OC9 --> OC10[Click Confirm Again]
        OC10 --> OC3
    end

    OrderConfirmation --> CRMUpdate2

    subgraph CRMUpdate2[" 🔄 CRM Stage Auto-Update (Won) "]
        direction TB
        CU21[Order Confirmed] --> CU22[Trigger: Auto-Update]
        CU22 --> CU23[Lead Stage → Won ✓]
        CU23 --> CU24[Lead Status → Won ✓]
    end

    CRMUpdate2 --> OrderFulfillment

    subgraph OrderFulfillment[" 📦 Order Fulfillment "]
        direction TB
        OF1[Order Confirmed] --> OF2{Product Type}

        OF2 --> OF2a[Storable Products]
        OF2 --> OF2b[Service Products]
        OF2 --> OF2c[Kit/BoM Products]

        OF2a --> OF3a[Delivery Order Created]
        OF3a --> OF3a1[Pick Products]
        OF3a1 --> OF3a2[Validate Delivery]

        OF2b --> OF3b[No Delivery Needed]

        OF2c --> OF3c[Manufacturing Order Created]
        OF3c --> OF3c1[Produce/Assemble]
        OF3c1 --> OF3c2[Validate Production]
        OF3c2 --> OF3a

        OF3a2 --> OF4[Delivery Complete ✓]
        OF3b --> OF4
    end

    OrderFulfillment --> Invoicing

    subgraph Invoicing[" 💵 Invoicing "]
        direction TB
        IN1[Click: Create Invoice] --> IN2{Invoice Inherits}

        IN2 --> IN2a[Customer Details]
        IN2 --> IN2b[Order Lines + Sequences]
        IN2 --> IN2c[VAT Type]
        IN2 --> IN2d[Email Thread Info ✓]
        IN2 --> IN2e[Approval Tracking ✓]

        IN2a --> IN3[Review Invoice]
        IN2b --> IN3
        IN2c --> IN3
        IN2d --> IN3
        IN2e --> IN3

        IN3 --> IN4{Margin Visible?}
        IN4 -->|For Authorized Users| IN5a[View Cost & Margin]
        IN4 -->|For Others| IN5b[Hidden]

        IN5a --> IN6[Confirm Invoice]
        IN5b --> IN6

        IN6 --> IN7[Status: Posted]
        IN7 --> IN8[Send Invoice Email<br/>Same Thread ✓]
    end

    Invoicing --> Payment

    subgraph Payment[" 💰 Payment Collection "]
        direction TB
        PY1[Customer Receives Invoice] --> PY2{Payment Method}

        PY2 --> PY2a[Bank Transfer]
        PY2 --> PY2b[Check]
        PY2 --> PY2c[Cash]
        PY2 --> PY2d[Credit Card]

        PY2a --> PY3[Register Payment]
        PY2b --> PY3
        PY2c --> PY3
        PY2d --> PY3

        PY3 --> PY4{Full Payment?}

        PY4 -->|Yes| PY5a[Invoice: Paid ✓]
        PY5a --> PY5a1[Credit Limit Freed]

        PY4 -->|Partial| PY5b[Invoice: Partially Paid]
        PY5b --> PY5b1[Wait for Remaining]

        PY4 -->|No Payment| PY5c{Overdue?}
        PY5c -->|Yes| PY5c1[Mark Overdue<br/>Follow Up]
        PY5c -->|Not Yet Due| PY5c2[Monitor Due Date]
    end

    Payment --> CycleComplete

    subgraph CycleComplete[" ✅ Cycle Complete "]
        direction TB
        CC1[Transaction Complete] --> CC2{Review Cycle}

        CC2 --> CC2a[✓ Partner Approved]
        CC2 --> CC2b[✓ Product Approved]
        CC2 --> CC2c[✓ Lead to Won]
        CC2 --> CC2d[✓ Email Thread Maintained]
        CC2 --> CC2e[✓ Validations Passed/Approved]
        CC2 --> CC2f[✓ Order Fulfilled]
        CC2 --> CC2g[✓ Invoice Sent]
        CC2 --> CC2h[✓ Payment Received]

        CC2a --> CC3[Success! ✓]
        CC2b --> CC3
        CC2c --> CC3
        CC2d --> CC3
        CC2e --> CC3
        CC2f --> CC3
        CC2g --> CC3
        CC2h --> CC3
    end

    CycleComplete --> Reporting

    subgraph Reporting[" 📊 Reporting & Analytics "]
        direction TB
        RP1{Generate Reports} --> RP1a[Sales Analysis]
        RP1 --> RP1b[Margin Analysis<br/>For Authorized]
        RP1 --> RP1c[Customer Payment Aging]
        RP1 --> RP1d[Tax Reports by VAT Type]
        RP1 --> RP1e[Approval History Audit]
        RP1 --> RP1f[CRM Conversion Rates]

        RP1a --> RP2[Management Review]
        RP1b --> RP2
        RP1c --> RP2
        RP1d --> RP2
        RP1e --> RP2
        RP1f --> RP2
    end

    Reporting --> NextCustomer([Ready for Next Customer 🔄])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style NextCustomer fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style SystemReady fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style MasterDataOps fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style CustomerInquiry fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style QuotationPrep fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style OrderConfirmation fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
    style OrderFulfillment fill:#558B2F,stroke:#fff,stroke-width:2px,color:#fff
    style Invoicing fill:#5E35B1,stroke:#fff,stroke-width:2px,color:#fff
    style Payment fill:#2E7D32,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 📅 Daily Operations Flowchart

### Daily Tasks for Different User Roles

```mermaid
flowchart TB
    Start([Start of Business Day]) --> RoleCheck

    subgraph RoleCheck[" 👤 User Role Check "]
        direction TB
        RC1{User Role} --> RC2a[Approver]
        RC1 --> RC2b[Salesperson]
        RC1 --> RC2c[Finance]
        RC1 --> RC2d[Admin]
    end

    RoleCheck --> ApproverTasks

    subgraph ApproverTasks[" ✅ Approver Daily Tasks "]
        direction TB
        AT1[Check Pending Approvals] --> AT2{Approval Type}

        AT2 --> AT2a[Partner Approvals]
        AT2 --> AT2b[Product Approvals]
        AT2 --> AT2c[Sales Validations]

        AT2a --> AT3a[Review Partner Details]
        AT3a --> AT3a1{Documents Present?}
        AT3a1 -->|Yes| AT3a2[Approve ✓]
        AT3a1 -->|No| AT3a3[Approve Anyway or Reject]

        AT2b --> AT3b[Review Product Details]
        AT3b --> AT3b1{Catalogs Uploaded?}
        AT3b1 -->|Yes| AT3b2{Pricing OK?}
        AT3b2 -->|Yes| AT3b3[Approve ✓]
        AT3b2 -->|No| AT3b4[Reject]
        AT3b1 -->|No| AT3b4

        AT2c --> AT3c[Review Sales Order]
        AT3c --> AT3c1{GP Margin Review}
        AT3c1 --> AT3c1a{Acceptable?}
        AT3c1a -->|Yes| AT3c2[Approve GP ✓]
        AT3c1a -->|No| AT3c3[Reject or Request Price Increase]

        AT3c --> AT3c4{Credit Limit Review}
        AT3c4 --> AT3c4a{Accept Risk?}
        AT3c4a -->|Yes| AT3c5[Approve Credit ✓]
        AT3c4a -->|No| AT3c6[Reject or Request Payment]

        AT3c --> AT3c7{Payment Terms Review}
        AT3c7 --> AT3c7a{Acceptable?}
        AT3c7a -->|Yes| AT3c8[Approve Payment Terms ✓]
        AT3c7a -->|No| AT3c9[Reject or Request Settlement]

        AT3a2 --> AT4[All Approvals Processed ✓]
        AT3a3 --> AT4
        AT3b3 --> AT4
        AT3b4 --> AT4
        AT3c2 --> AT4
        AT3c3 --> AT4
        AT3c5 --> AT4
        AT3c6 --> AT4
        AT3c8 --> AT4
        AT3c9 --> AT4
    end

    ApproverTasks --> SalespersonTasks

    subgraph SalespersonTasks[" 💼 Salesperson Daily Tasks "]
        direction TB
        ST1[Review My Pipeline] --> ST2{CRM Leads}

        ST2 --> ST2a[New Leads]
        ST2a --> ST2a1[Contact Customer]
        ST2a1 --> ST2a2[Send Initial Email<br/>Thread Created ✓]

        ST2 --> ST2b[Leads: Quotation Sent]
        ST2b --> ST2b1[Follow Up]
        ST2b1 --> ST2b2{Response?}
        ST2b2 -->|Yes| ST2b3[Create/Update Quotation]
        ST2b2 -->|No| ST2b4[Send Reminder]

        ST2 --> ST2c[Leads: Won]
        ST2c --> ST2c1[Process Orders]

        ST3[Create Quotations] --> ST3a[From Leads]
        ST3a --> ST3b[Add Approved Products]
        ST3b --> ST3c[Check Price History]
        ST3c --> ST3d[Send to Customer<br/>Same Thread ✓]

        ST4[Confirm Orders] --> ST4a{Validations?}
        ST4a -->|Triggered| ST4a1[Send for Approval]
        ST4a1 --> ST4a2[Wait for Approval]
        ST4a2 --> ST4a3[Confirm After Approval]
        ST4a -->|Passed| ST4a4[Confirm Immediately]

        ST5[Follow Up Orders] --> ST5a[Check Delivery Status]
        ST5a --> ST5b[Coordinate with Warehouse]

        ST6[Invoice Follow Up] --> ST6a[Send Invoices<br/>Same Thread ✓]
        ST6a --> ST6b[Payment Follow Up]

        ST2a2 --> ST7[Daily Tasks Complete ✓]
        ST2b3 --> ST7
        ST2b4 --> ST7
        ST2c1 --> ST7
        ST3d --> ST7
        ST4a3 --> ST7
        ST4a4 --> ST7
        ST5b --> ST7
        ST6b --> ST7
    end

    SalespersonTasks --> FinanceTasks

    subgraph FinanceTasks[" 💰 Finance Daily Tasks "]
        direction TB
        FT1[Review Financials] --> FT2{Daily Checks}

        FT2 --> FT2a[Credit Limit Monitoring]
        FT2a --> FT2a1{Customers Near Limit?}
        FT2a1 -->|Yes| FT2a2[Alert Salesperson]
        FT2a1 -->|No| FT2a3[All Good ✓]

        FT2 --> FT2b[Payment Aging]
        FT2b --> FT2b1{Overdue Invoices?}
        FT2b1 -->|Yes| FT2b2[Follow Up Collection]
        FT2b1 -->|No| FT2b3[All Good ✓]

        FT2 --> FT2c[Tax Reports]
        FT2c --> FT2c1[Review VAT Transactions]
        FT2c --> FT2c2[Review SVAT Transactions]
        FT2c --> FT2c3[Review GST Transactions]

        FT3[Payment Registration] --> FT3a[Record Bank Transfers]
        FT3a --> FT3b[Record Checks]
        FT3b --> FT3c[Reconcile Accounts]

        FT4[Margin Analysis] --> FT4a[Review Order Margins]
        FT4a --> FT4b[Review Invoice Margins]
        FT4b --> FT4c{Below Threshold?}
        FT4c -->|Yes| FT4c1[Alert Management]
        FT4c -->|No| FT4c2[All Good ✓]

        FT2a2 --> FT5[Finance Tasks Complete ✓]
        FT2a3 --> FT5
        FT2b2 --> FT5
        FT2b3 --> FT5
        FT2c3 --> FT5
        FT3c --> FT5
        FT4c1 --> FT5
        FT4c2 --> FT5
    end

    FinanceTasks --> AdminTasks

    subgraph AdminTasks[" ⚙️ Admin Daily Tasks "]
        direction TB
        AD1[System Monitoring] --> AD2{Daily Checks}

        AD2 --> AD2a[Auto-Close Cron]
        AD2a --> AD2a1{Leads Auto-Closed?}
        AD2a1 -->|Yes| AD2a2[Review Closed Leads]
        AD2a1 -->|No| AD2a3[Cron Running OK ✓]

        AD2 --> AD2b[Partner Document Status]
        AD2b --> AD2b1{Partners: Pending Document?}
        AD2b1 -->|Yes| AD2b2[Alert Partners]
        AD2b1 -->|No| AD2b3[All Good ✓]

        AD2 --> AD2c[Approval Backlogs]
        AD2c --> AD2c1{Pending > 3 Days?}
        AD2c1 -->|Yes| AD2c2[Alert Approvers]
        AD2c1 -->|No| AD2c3[All Good ✓]

        AD3[User Support] --> AD3a[Answer User Questions]
        AD3a --> AD3b[Resolve Issues]
        AD3b --> AD3c[Update Documentation]

        AD4[Master Data Maintenance] --> AD4a[Add New Business Nature]
        AD4a --> AD4b[Add New Brands]
        AD4b --> AD4c[Update Categories]
        AD4c --> AD4d[Maintain Tax Types]

        AD2a2 --> AD5[Admin Tasks Complete ✓]
        AD2a3 --> AD5
        AD2b2 --> AD5
        AD2b3 --> AD5
        AD2c2 --> AD5
        AD2c3 --> AD5
        AD3c --> AD5
        AD4d --> AD5
    end

    AdminTasks --> EndOfDay

    subgraph EndOfDay[" 🌙 End of Day "]
        direction TB
        ED1[Daily Summary] --> ED2{Reports}

        ED2 --> ED2a[Sales Today]
        ED2 --> ED2b[Quotations Sent]
        ED2 --> ED2c[Orders Confirmed]
        ED2 --> ED2d[Invoices Created]
        ED2 --> ED2e[Payments Received]
        ED2 --> ED2f[Pending Approvals]

        ED2a --> ED3[Management Dashboard]
        ED2b --> ED3
        ED2c --> ED3
        ED2d --> ED3
        ED2e --> ED3
        ED2f --> ED3

        ED3 --> ED4[Day Complete ✓]
    end

    EndOfDay --> Complete([Ready for Tomorrow 🚀])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style Complete fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style RoleCheck fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style ApproverTasks fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style SalespersonTasks fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style FinanceTasks fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style AdminTasks fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
    style EndOfDay fill:#2E7D32,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 🔧 Troubleshooting Decision Flowchart

### Common Issues and Resolution Paths

```mermaid
flowchart TB
    Start([User Encounters Issue]) --> IssueType

    subgraph IssueType[" ⚠️ Issue Type "]
        direction TB
        IT1{What's the Problem?} --> IT2a[Cannot Add Product to Order]
        IT1 --> IT2b[Partner Status: Pending Document]
        IT1 --> IT2c[Order Stuck in Pending]
        IT1 --> IT2d[Wrong Tax Applied]
        IT1 --> IT2e[Email Thread Not Working]
        IT1 --> IT2f[Credit Limit Exceeded]
        IT1 --> IT2g[Product Catalog Required Error]
        IT1 --> IT2h[CRM Stage Not Updating]
    end

    IssueType --> ProductIssue

    subgraph ProductIssue[" 📦 Product Cannot Be Added "]
        direction TB
        PI1[Error: Product Must Be Approved] --> PI2{Check Product State}

        PI2 --> PI3a[State: Draft]
        PI3a --> PI4a{Catalogs Uploaded?}
        PI4a -->|No| PI5a[Upload Product Catalogs]
        PI5a --> PI6a[Request Approval]
        PI4a -->|Yes| PI6a

        PI2 --> PI3b[State: Waiting Approval]
        PI3b --> PI4b[Contact Approver]
        PI4b --> PI5b[Expedite Approval]

        PI2 --> PI3c[State: Rejected]
        PI3c --> PI4c[Review Rejection Reason]
        PI4c --> PI5c[Fix Issues]
        PI5c --> PI6c[Request Approval Again]

        PI6a --> PI7[Wait for Approval]
        PI5b --> PI7
        PI6c --> PI7

        PI7 --> PI8[Product: Approved ✓]
        PI8 --> PI9[Retry Adding to Order]
        PI9 --> PI10[Success ✓]
    end

    IssueType --> PartnerDocIssue

    subgraph PartnerDocIssue[" 📄 Partner Pending Document "]
        direction TB
        PD1[Status: Pending Document] --> PD2{Within Grace Period?}

        PD2 -->|Yes| PD3[Upload Documents:]
        PD3 --> PD3a[Business Reg Attachments]
        PD3 --> PD3b[VAT Reg Attachments]
        PD3 --> PD3c[Customer Reg Attachments]

        PD3a --> PD4[Click: State For Approved]
        PD3b --> PD4
        PD3c --> PD4

        PD4 --> PD5[Status: Approved ✓]

        PD2 -->|No - Expired| PD6[Status: Approved Without Doc]
        PD6 --> PD7[Upload Documents]
        PD7 --> PD8[Contact Administrator]
        PD8 --> PD9[Admin Resets Status]
        PD9 --> PD5
    end

    IssueType --> OrderPendingIssue

    subgraph OrderPendingIssue[" ⏳ Order Stuck in Pending "]
        direction TB
        OP1[Status: Pending] --> OP2{Check Triggered Validations}

        OP2 --> OP3a{GP Margin Triggered?}
        OP3a -->|Yes| OP4a[Send for GP Margin Approval]
        OP4a --> OP5a[Select GP Margin Approver]

        OP2 --> OP3b{Credit Limit Triggered?}
        OP3b -->|Yes| OP4b[Send for Credit Limit Approval]
        OP4b --> OP5b[Select Credit Limit Approver]

        OP2 --> OP3c{Payment Terms Triggered?}
        OP3c -->|Yes| OP4c[Send for Payment Term Approval]
        OP4c --> OP5c[Select Payment Term Approver]

        OP2 --> OP3d{Multiple Triggered?}
        OP3d -->|Yes| OP4d[Send for All Validations Approval]
        OP4d --> OP5d[Select All Validations Approver]

        OP5a --> OP6[Approver Approves]
        OP5b --> OP6
        OP5c --> OP6
        OP5d --> OP6

        OP6 --> OP7[Status: Approved]
        OP7 --> OP8[Click: Confirm Again]
        OP8 --> OP9[Order Confirmed ✓]
    end

    IssueType --> TaxIssue

    subgraph TaxIssue[" 💰 Wrong Tax Applied "]
        direction TB
        TI1[Wrong Tax on Order] --> TI2{Check Customer VAT Type}

        TI2 --> TI3[Open Customer Record]
        TI3 --> TI4{VAT Type Correct?}

        TI4 -->|No| TI5[Update Customer VAT Type]
        TI5 --> TI6[Save Customer]

        TI4 -->|Yes| TI7[Open Sales Order]

        TI6 --> TI7

        TI7 --> TI8[Change VAT Type Field]
        TI8 --> TI9[System Recalculates Taxes ✓]

        TI9 --> TI10{Verify Tax}
        TI10 --> TI11[Correct Tax Applied ✓]
    end

    IssueType --> EmailThreadIssue

    subgraph EmailThreadIssue[" 📧 Email Thread Not Working "]
        direction TB
        ET1[Thread Not Continuing] --> ET2{Created from Lead?}

        ET2 -->|No| ET3[Problem: Manual Quotation]
        ET3 --> ET4[Solution: Always use<br/>New Quotation button from Lead]

        ET2 -->|Yes| ET5{Email Sent from Lead First?}

        ET5 -->|No| ET6[Problem: No Message-ID]
        ET6 --> ET7[Solution: Send at least one<br/>email from Lead before<br/>creating Quotation]

        ET5 -->|Yes| ET8{Module Installed?}

        ET8 -->|No| ET9[Install lablink_mail_thread]
        ET9 --> ET10[Update Module]

        ET8 -->|Yes| ET11{Check Fields}

        ET11 --> ET12[Open Lead in Debug Mode]
        ET12 --> ET13{email_thread_id populated?}

        ET13 -->|No| ET14[Thread Not Captured]
        ET14 --> ET15[Send Email from Lead]
        ET15 --> ET16[Thread Captured ✓]

        ET13 -->|Yes| ET17[Thread Should Work ✓]
        ET17 --> ET18[Check Customer Email Client]
    end

    IssueType --> CreditIssue

    subgraph CreditIssue[" 💳 Credit Limit Exceeded "]
        direction TB
        CI1[Credit Limit Exceeded] --> CI2{Resolution Options}

        CI2 --> CI3a[Option 1:<br/>Increase Credit Limit]
        CI3a --> CI4a[Open Customer]
        CI4a --> CI5a[Increase Credit Limit Field]
        CI5a --> CI6a[Save]
        CI6a --> CI7a[Retry Confirm Order]

        CI2 --> CI3b[Option 2:<br/>Request Approval Override]
        CI3b --> CI4b[Send for Credit Limit Approval]
        CI4b --> CI5b[Approver Accepts Risk]
        CI5b --> CI6b[Order Approved]
        CI6b --> CI7b[Confirm Order]

        CI2 --> CI3c[Option 3:<br/>Collect Payment First]
        CI3c --> CI4c[Contact Customer]
        CI4c --> CI5c[Receive Payment]
        CI5c --> CI6c[Register Payment]
        CI6c --> CI7c[Credit Limit Freed]
        CI7c --> CI7d[Retry Confirm Order]

        CI7a --> CI8[Order Confirmed ✓]
        CI7b --> CI8
        CI7d --> CI8
    end

    IssueType --> CatalogIssue

    subgraph CatalogIssue[" 📁 Product Catalog Required "]
        direction TB
        CA1[Error: Catalog Required] --> CA2[Open Product Form]

        CA2 --> CA3[Scroll to:<br/>Product Catalogs Section]

        CA3 --> CA4[Click: Upload/Add a file]

        CA4 --> CA5{Upload Files}

        CA5 --> CA5a[Product Brochure PDF]
        CA5 --> CA5b[Datasheet]
        CA5 --> CA5c[Technical Specs]
        CA5 --> CA5d[User Manual]

        CA5a --> CA6[Files Attached ✓]
        CA5b --> CA6
        CA5c --> CA6
        CA5d --> CA6

        CA6 --> CA7[Save Product]
        CA7 --> CA8[Request Approval]
        CA8 --> CA9[Approval Works ✓]
    end

    IssueType --> CRMStageIssue

    subgraph CRMStageIssue[" 🔄 CRM Stage Not Updating "]
        direction TB
        CS1[Stage Not Auto-Updating] --> CS2{Check Configuration}

        CS2 --> CS3[Settings → CRM Settings]

        CS3 --> CS4{State After Quotation Set?}

        CS4 -->|No| CS5[Select CRM Stage]
        CS5 --> CS6[Save Settings]

        CS4 -->|Yes| CS7{Stage Exists?}

        CS7 -->|No| CS8[CRM → Configuration → Stages]
        CS8 --> CS9[Create Missing Stage]
        CS9 --> CS10[Save Stage]

        CS7 -->|Yes| CS11{Same After Order?}

        CS11 --> CS12[Check:<br/>State After Sale Order Confirmation]
        CS12 --> CS13{Set?}

        CS13 -->|No| CS14[Select Stage]
        CS14 --> CS15[Save]

        CS13 -->|Yes| CS16[Configuration OK ✓]

        CS6 --> CS17[Auto-Update Works ✓]
        CS10 --> CS17
        CS15 --> CS17
        CS16 --> CS17

        CS17 --> CS18[Retry Creating Quotation/Order]
        CS18 --> CS19[Stage Updates ✓]
    end

    ProductIssue --> IssueResolved
    PartnerDocIssue --> IssueResolved
    OrderPendingIssue --> IssueResolved
    TaxIssue --> IssueResolved
    EmailThreadIssue --> IssueResolved
    CreditIssue --> IssueResolved
    CatalogIssue --> IssueResolved
    CRMStageIssue --> IssueResolved

    subgraph IssueResolved[" ✅ Issue Resolved "]
        direction TB
        IR1[Issue Fixed ✓] --> IR2[Test Solution]
        IR2 --> IR3{Works?}

        IR3 -->|Yes| IR4[Continue Normal Operations]
        IR3 -->|No| IR5[Contact Support]

        IR5 --> IR6[Provide Details:<br/>- Issue description<br/>- Steps taken<br/>- Screenshots<br/>- Error messages]

        IR6 --> IR7[Support Assists]
        IR7 --> IR4
    end

    IssueResolved --> Complete([Problem Solved 🎉])

    style Start fill:#714B67,stroke:#fff,stroke-width:3px,color:#fff
    style Complete fill:#2E7D32,stroke:#fff,stroke-width:3px,color:#fff
    style IssueType fill:#1565C0,stroke:#fff,stroke-width:2px,color:#fff
    style ProductIssue fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style PartnerDocIssue fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style OrderPendingIssue fill:#D84315,stroke:#fff,stroke-width:2px,color:#fff
    style TaxIssue fill:#00838F,stroke:#fff,stroke-width:2px,color:#fff
    style EmailThreadIssue fill:#558B2F,stroke:#fff,stroke-width:2px,color:#fff
    style CreditIssue fill:#5E35B1,stroke:#fff,stroke-width:2px,color:#fff
    style CatalogIssue fill:#F57C00,stroke:#fff,stroke-width:2px,color:#fff
    style CRMStageIssue fill:#6A1B9A,stroke:#fff,stroke-width:2px,color:#fff
    style IssueResolved fill:#2E7D32,stroke:#fff,stroke-width:2px,color:#fff
```

---

## 📄 Document Information

| Field | Value |
|-------|-------|
| **Document** | LabLink Complete Flowchart Guide |
| **Purpose** | Comprehensive flowcharts for all configurations and workflows |
| **Odoo Version** | 18.0 |
| **Last Updated** | 2025-01-18 |
| **Version** | 1.0 |
| **Prepared By** | Centrics Development Team |

---

<div align="center">

**For detailed documentation, see:**
- [LabLink Custom Developments Manual](./LabLink_Custom_Developments_Manual.md)
- [LabLink Workflows & Configuration Guide](./LabLink_Workflows_Configuration_Guide.md)

---

![Odoo](https://img.shields.io/badge/Complete-Flowcharts-714B67?style=for-the-badge&logo=odoo&logoColor=white)
![Visual](https://img.shields.io/badge/All-Workflows-success?style=for-the-badge)

**All flowcharts optimized for GitHub Dark Mode** 🌙

</div>
