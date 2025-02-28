---
layout: default
title: On Shaping the Future of Testing & Developer Productivity
description: 
---

# Hello Niranjan,  

I'm excited about the [opportunity][job] at Coinbase and wanted to share my thoughts on [your recent post][post].  

## Why I'm Passionate About This Position 💪🏾
Throughout my career, I have always gravitated toward what I coined "libraries, frameworks, and utilities." I have always found satisfaction in making the lives of my fellow engineers easier. This has often manifested in testing, which I take seriously. 

### **Examples of Personal Projects**:
- 📈 **Apache NiFi Data Flow:** Developed a human-readable to binary converter for a legacy format, making tests more readable and flexible.  
- 🐦 **Twitter Developer Platform:** Automated test user creation, credential storage, and retrieval for testing saving collegues developer time.
- 🍿 **Netflix:** While working in the Developer Productivity org I researched JavaScript test frameworks and standards in the company and wrote the first test for a metrics dashboard written in TypeScript used by the Consumer Engineering organization.  

My career has increasingly focused on the areas of testing infrastructure & developer productivity as I will describe below.

---

## **My Insights & Contributions**  
Below are my thoughts on the responsibilities outlined in your post.  

### **Improve Testing Reliability and Speed 🏃🏾‍♂️** 
As test execution moves closer to a real system, it inevitably becomes more flaky. Many system/integration tests suffer from this issue, often addressed through retries and other strategies to filter out false failures.  

#### **Key Areas of Focus**:
- 📊 **Test Execution Time Metrics:** Many frameworks generate this data, which we can track and provide as feedback throughout the development lifecycle.  We can also use this data as a basis for setting OKRs and org / company wide goals. 
- 🛠️ **Mocking Dependencies:** Explore opportunities to mock external dependencies (e.g., **Testcontainers, Devcontainers**) to improve reliability.  
- ▶️ **Record and Replay** - Capture real production traffic and efficiently replay it in a local test environment to enhance speed and reliability.
- ⏳ **Performance Profiling:** Identify bottlenecks in tests and establish best practices for optimizing test execution time.  
-  🔄 **Shift-Left Testing:** Introduce testing strategies earlier in the development cycle to catch issues sooner and reduce costly late-stage debugging.  

---

### **Automate Testing at Every Level ⚙️**  
One of the first challenges will be the **lack of universal definitions** for unit, integration, system, and end-to-end tests. Surprisingly, this varies across organizations and even within different teams (frontend, backend, and language-specific ecosystems).  

#### **How to Address This**:
- 📖 **Define Test Types:** Establish a **clear company-wide definition** of different test levels.  
- 🎯 **Common Vocabulary:** Encourage discussion and iteration to refine these definitions, ensuring alignment across teams.  
- 🚀 **Best Practices:** Use these definitions to guide **test strategy, automation, and tooling** for each level.  

---

### **Flaky Test Detection, Self-Healing Automation & Anomaly Detection 🤖**  
Flaky tests create **frustration and inefficiency** and also decreases developer trust in my their test suites.

Due to the potential size of the team, deciding whether to **build in-house solutions** or **use external vendors** is a key strategic decision.  

#### **Considerations**:
- 💰 **Vendor Solutions:** Some organizations use **third-party tools** (e.g., **Gradle Enterprise, etc**) to provide **flaky test detection, selective test execution, and remote test execution** without heavy internal investment.  
- 🏗️ **Building In-House:** If internal investment makes sense, we should determine the **most critical test reliability issues** to tackle first, given team capacity and company goals.  
 🔍 Cost vs. Flexibility Trade-offs: Weigh the long-term benefits of in-house development (customization, integration) versus vendor solutions (faster setup, ongoing costs, support).

---

### **Remove Bottlenecks, Introduce Smart Developer Tools & Boost Engineering Productivity 🚀**  
Create developer personas and understand deeply the developer workflow in used ecosystems in the comapny.  Get anecdotal evidence of problem poiints through interviews.  Look at the metrics to see where is the longest parts of the development loop.


Some areas of Exploration:
- ⚡ **Build & Test Parallelization**: Speed up development cycles by running tests and builds in parallel wherever possible.

- 🔄 **CI/CD Improvements**: Reduce friction in deployments by optimizing test suites, ensuring faster feedback loops, and minimizing redundant runs.

- 🏗️ **Local Development Enhancements**: Provide engineers with better local testing environments, reducing the need for costly remote debugging.

- 📊 **Developer Workflow Metrics**: Capture data on developer interactions with CI/CD systems to identify and resolve workflow inefficiencies.

---

### **Establish Quality Metrics That Drive Product Stability & Efficiency 📊**  
Quality metrics provide actionable insights, but **standardization across testing frameworks is inconsistent**. Many frameworks attempt to support formats like `junit.xml`, but **there is no true standard**, leading to fragmented data collection.  My first aim would be to understand the various paved path ecosystems at Coinbase and analyze the best approach for common metrics across all paved path ecosystems.

#### **Key Focus Areas**:
- 📊 **Open Test Formats:** Investigate efforts like [The Open Test Reporting format][open-test-reporting-format] to establish **cross-framework test result standards**.  
- 📡 **Infrastructure for Metrics:** Ensure we have a **reliable system for capturing, storing, and presenting test data** to enable leadership decision-making.  
- 🎯 **Defining Focus Metrics:** Identify **which test-related metrics** (flakiness rate, execution time, coverage) are most critical to improving product quality.  
- 📈 **Actionable Insights:** Translate collected metrics into concrete improvements, such as optimizing slow test suites or identifying trends in flaky test failures.

---

### **Partner with Teams Across the Company to Drive Best Practices & Make an Impact Company-Wide 🤝**  
- 📚 **Documentation & Training:** Create **clear guides and resources** to help teams adopt best testing practices.  
- 🏋🏾 **Hands-On Support:** Work directly with teams to implement, debug, and improve testing strategies** based on their specific needs.  
- 💡 **Internal Advocacy:** Establish regular discussions and knowledge-sharing sessions to align teams on best practices.  

---

## **📩 Let's Connect & Continue the Conversation**  
**Bobby Owolabi**  
📄 [Resume Download][resume-download]  
✉️ bobby@bobbyowolabi.com <br/>
🌐 [bobbyowolabi.com](https://www.bobbyowolabi.com/)  
🔗 [Connect on LinkedIn](https://linkedin.com/in/bobbyowolabi)



[post]: https://www.linkedin.com/posts/niranjanprithviraj_software-engineer-frontend-consumer-ceti-activity-7300564482466938882-EzOU
[resume-download]: https://drive.google.com/file/d/1H-a-Q2rRVj9nAPh1qad4CvTfojAlZ7GP/view?usp=sharing
[open-test-reporting-format]: https://github.com/orgs/junit-team/projects/4/views/1?pane=issue&itemId=86522386&issue=junit-team%7Cjunit5%7C4113
[job]: https://www.coinbase.com/careers/positions/6202747