# Union-under-Duress: Understanding Hazards of Duplicate Resource Mismediation in Android Software Supply Chain

## Overview
This repository serves as a hub for discussing and understanding the significant security risks associated with duplicate resource mismediation (Duress) in the Android software supply chain. Our research, detailed in the paper "Union under Duress," uncovers a new attack surface that poses serious threats to Android applications.

**Website with attack demo video**: [Union under Duress](https://sites.google.com/view/union-under-duress/attack-demo)

## Vendor Response
Despite the potential severity of these findings, the response from Google has been underwhelming. They have not recognized this as a security issue within the scope of the Android Studio, instead labeling it as a responsibility of developers to ensure the security of their supply chain. Google's response can be found on our [Response Page](https://sites.google.com/view/union-under-duress/responses).

## Abstract Overview

1. These attacks do not employ malicious code; instead, they leverage customized resources in the library(string, config files, etc.) to execute stealthy attacks.
2. When there are conflicting resources from multiple libraries, the resources from lower-priority library will be abandon by Android resource compiler(ARC). The resources from the higher-priority library will take precedence and be included in the final app.
3. ARC's priority mechanism determines the priority of libraries based on their dependency relation and position in dependency list.
4. The study is the first systematic investigation into Duress risks, analyzing over 23,000 libraries and 150,000 apps. It finds that 18.4% of libraries have sensitive resources exposed to Duress risks, 25.7% have integration risks with duplicate sensitive resources, and over 400 apps are potentially affected by Duress​.

### Duplication Resource Mismediation (Duress):

1. Duress arises due to the lack of information about individual libraries' trustworthiness and the absence of isolation between library resources during the build process.
2. Attackers can exploit ARC to override or merge resources of victim libraries with those from malicious libraries, leading to security breaches such as redirecting data to servers controlled by adversaries.

### Attack Strategies:

1. Attackers can raise the priority of their malicious libraries, allowing them to override resources in lower-priority, legitimate libraries.
2. Real-world examples include overriding the CDN URL of Razorpay, a payment platform, and replacing AWS credentials in the MistPlay SDK. 

### Methodology and Analysis:

1. The study identifies sensitive resource types and analyzes libraries and apps to assess Duress risks.
2. Sensitive resources include manifest attributes and developer-specified resources like backend URLs, credentials, and technical support messages.
3. The analysis reveals that 18.4% of libraries contain sensitive resources vulnerable to Duress attacks. Integration risks are found in 25.7% of libraries, and at least 428 apps are potentially already affected by Duress.
4. Notably, network security configurations and file provider paths are among the most common sources of integration risks​​.

## Resources
For a deeper understanding and demonstration of the issue, please refer to the following resources:
- **Demo Video**: [Attack Demonstration](https://sites.google.com/view/union-under-duress/attack-demo)
- **Research Paper**: [Download PDF](./original_paper.pdf)
- **Presentation Slides**: [View Slides](./slides.pdf)
