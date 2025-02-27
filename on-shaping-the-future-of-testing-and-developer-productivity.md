---
layout: default
title: On Shaping the Future of Testing & Developer Productivity
description: 
---

# Hello Niranjan,  

I'm excited about the opportunity at Coinbase and wanted to share my thoughts on [your recent post][post].  

## Why I'm Passionate About This Position 💪🏾
Throughout my career, I have always gravitated toward what I coined **"libraries, frameworks, and utilities."**  
I have always found satisfaction in making the lives of my fellow engineers easier. This has often manifested in testing, which I take seriously.  

### **Examples of My Unasked Contributions**:
- 📈 **Apache NiFi Data Flow:** Developed a **human-readable to binary converter** for a legacy format, making tests more readable and flexible.  
- 🐦 **Twitter Developer Platform:** Automated **test user creation, credential storage, and retrieval** for testing saving collegues developer time.
- 🍿 **Netflix (Developer Productivity):** Researched **JavaScript test frameworks** and wrote the **first test** for a metrics dashboard written in TypeScript used by the Consumer Engineering organization.  

My experience has increasingly focused on this area, as I will describe below and can be viewed in my resume.

---

## **My Insights & Contributions**  
Below are my thoughts on the responsibilities outlined in your post.  

### **Improve Testing Reliability and Speed 🏃🏾‍♂️** 
As test execution moves closer to a real system, it **inevitably becomes more flaky**. Many system/integration tests suffer from this issue, often addressed through retries and other strategies to filter out false failures.  

#### **Key Areas of Focus**:
- 📊 **Test Execution Time Metrics:** Many frameworks generate this data, which we can **track and provide as feedback** throughout the development lifecycle.  We can also use this data as a basis for setting OKRs and org / company wide goals. 
- 🛠️ **Mocking Dependencies:** Explore opportunities to **mock external dependencies** (e.g., **Testcontainers, Devcontainers**) to improve reliability.  
- Record / Replay - recording actual production traffic so it can be replayed locally in a test.
- ⏳ **Performance Profiling:** Identify bottlenecks in tests and establish **best practices** for optimizing test execution time.  
-  🔄 **Shift-Left Testing:** Introduce testing strategies earlier in the development cycle to **catch issues sooner** and reduce costly late-stage debugging.  

---

### **Automate Testing at Every Level ⚙️**  
One of the first challenges will be the **lack of universal definitions** for unit, integration, system, and end-to-end tests. Surprisingly, this varies across organizations and even within different teams (frontend, backend, and language-specific ecosystems).  

#### **How to Address This**:
- 📖 **Define Test Types:** Establish a **clear company-wide definition** of different test levels.  
- 🎯 **Common Vocabulary:** Encourage discussion and iteration to refine these definitions, ensuring alignment across teams.  
- 🚀 **Best Practices:** Use these definitions to guide **test strategy, automation, and tooling** for each level.  

---

### **Flaky Test Detection, Self-Healing Automation & Anomaly Detection 🤖**  
Flaky tests create **frustration and inefficiency**. However, deciding whether to **build in-house solutions** or **use external vendors** is a key strategic decision.  

#### **Considerations**:
- 💰 **Vendor Solutions:** Some organizations use **third-party tools** (e.g., **Gradle Enterprise**) to provide **flaky test detection, selective test execution, and remote test execution** without heavy internal investment.  
- 🏗️ **Building In-House:** If internal investment makes sense, we should focus on **anomaly detection models** that proactively identify flakiness patterns.  
- 📈 **Prioritization:** Determine the **most critical test reliability issues** to tackle first, given team capacity and company goals.  

---

### **Remove Bottlenecks, Introduce Smart Developer Tools & Boost Engineering Productivity 🚀**  
*(This section needs expansion—perhaps mention areas like build/test parallelization, CI/CD improvements, or local dev tooling?)*  

---

### **Establish Quality Metrics That Drive Product Stability & Efficiency 📊**  
Quality metrics provide actionable insights, but **standardization across testing frameworks is inconsistent**. Many frameworks attempt to support formats like `JUnit.xml`, but **there is no true standard**, leading to fragmented data collection.  

#### **Key Focus Areas**:
- 📊 **Open Test Formats:** Investigate efforts like [insert link] to establish **cross-framework test result standards**.  
- 📡 **Infrastructure for Metrics:** Ensure we have a **reliable system for capturing, storing, and presenting test data** to enable leadership decision-making.  
- 🎯 **Defining Focus Metrics:** Identify **which test-related metrics** (flakiness rate, execution time, coverage) are most critical to improving product quality.  

---

### **Partner with Teams Across the Company to Drive Best Practices & Make an Impact Company-Wide 🤝**  
- 📚 **Documentation & Training:** Create **clear guides and resources** to help teams adopt best testing practices.  
- 🏋🏾 **Hands-On Support:** Work directly with teams to **implement, debug, and improve testing strategies** based on their specific needs.  
- 💡 **Internal Advocacy:** Establish **regular discussions and knowledge-sharing sessions** to align teams on best practices.  

---

## **📩 Let's Connect & Continue the Conversation**  
**[Bobby Owolabi]**  
📄 [Resume Download][resume-download]  
✉️ bobby@bobbyowolabi.com 
🌐 [bobbyowolabi.com](https://www.bobbyowolabi.com/)  
🔗 [Connect on LinkedIn](https://linkedin.com/in/bobbyowolabi)







### **Flaky Test Detection, Self-Healing Automation & Anomaly Detection 🤖**  
As a team, we have to look at what the priorities are and the capacity we have.  For instance, it may make sense to hire a vendor who has solved problems to provide a solution for us (may be cheaper thebn using our own developer hours).  For instance, I have seen an organization with a small engineering test team pay for Gradle enterprise to solve these pronblems.  We were able to get flaky test detection and selective test detection and remote test execution through outside vendor.  Depending on our situation it may make sense to invest in this functionality in house.

#### Remove bottlenecks, introduce smart developer tools, and boost engineering productivity.
(Please add something reasonable here)

#### Establish quality metrics that drive product stability and efficiency. 📊
Various test related merics available across frameworks.  I have  found that many test frameworks attempt to implement common metric file formations like Junit.xml .  this has been problematic because there is no standard.  That is why there are efforts for open test formats (insert link here).

Ernsure the infrastrire is in placed to capture store and present these metrics so that our leadership can make decisions of which metrics we should focus on improving across the organiation.

#### Partner with teams across the company to drive best practices and make an impact company-wide. 
documentation, training, hands on time with customer teams.

I would love to continue the conversation about the above and more.


[post]: https://www.linkedin.com/posts/niranjanprithviraj_software-engineer-frontend-consumer-ceti-activity-7300564482466938882-EzOU
[resume-download]: https://drive.google.com/file/d/1H-a-Q2rRVj9nAPh1qad4CvTfojAlZ7GP/view?usp=sharing