---
title: "Blog 1"
date: 2026-06-10
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
# [AI/DEV] KIRO – AWS'S AI CODING ASSISTANT AND THE TREND OF AI-ASSISTED DEVELOPMENT LIFECYCLE

Hello AWS Study Group VN!

Recently, AI coding assistants have become one of the biggest trends in software development. While developers previously relied on AI mainly for code completion, bug fixing, or error explanations, AI is now becoming involved throughout the entire software development lifecycle—from requirements analysis and system design to code generation, testing, documentation, and improving team productivity.

According to the AWS Architecture Blog introducing the updated **AWS Well-Architected Machine Learning Lens**, AWS highlighted a new approach called **AI-assisted development lifecycle**, which includes **code generation** and **productivity enhancement** through tools such as **Kiro** and **Amazon Q Developer**.

In this article, our team would like to introduce **Kiro**, AWS's AI coding assistant. Rather than viewing it simply as an AI that writes code, we'd like to explore it as a tool that supports a more structured and professional software development process.

---

# WHAT IS KIRO?

Kiro is an AI-powered IDE and coding assistant developed by AWS to help developers build software in a more structured and organized way.

Instead of generating code immediately from a prompt, Kiro encourages developers to follow a **Spec-Driven Development** workflow, where software is built based on well-defined specifications.

In simple terms, before writing any code, Kiro can help developers clarify questions such as:

- What problem does this feature solve?
- How will users interact with this feature?
- What are the detailed functional requirements?
- How should the technical design be structured?
- What implementation tasks are required?
- What test cases should be prepared?

This approach is particularly valuable because many real-world software projects fail not because of poor coding, but because requirements are unclear, designs are incomplete, and team members have different interpretations of the same feature.

---

# SPEC-DRIVEN DEVELOPMENT – ANALYZE BEFORE YOU CODE

One of Kiro's most notable features is its **Spec-Driven Development** workflow.

A common way people use AI today is something like:

> "Build me a login feature."

The AI immediately generates code, and developers simply keep fixing issues until it works.

While this approach is fast for small tasks, it often becomes problematic in larger projects because the AI may:

- Make incorrect assumptions about business logic
- Generate unnecessary files
- Produce implementations that don't fully match the original requirements

Kiro encourages a more systematic workflow:

1. Describe the idea or feature.
2. Generate detailed requirements.
3. Produce the technical design.
4. Break the work into implementation tasks.
5. Review and refine the specification.
6. Only then start generating code.

For example, instead of asking AI to immediately build a login feature, Kiro can first analyze the requirements:

- Users enter an email address and password.
- Validate user input.
- Display an error message for invalid credentials.
- Generate a session or authentication token after successful login.
- Restrict protected routes to authenticated users only.
- Create test cases covering successful login, failed login, and missing input scenarios.

As a result, the AI works from a complete specification rather than a short and ambiguous prompt.

---

# KIRO IN THE AI-ASSISTED DEVELOPMENT LIFECYCLE

According to the AWS Architecture Blog, the updated **AWS Well-Architected Machine Learning Lens** introduces new guidance around the **AI-assisted development lifecycle**, highlighting **code generation** and **developer productivity** through tools like **Kiro** and **Amazon Q Developer**.

This demonstrates that AWS no longer views AI coding assistants as simple code-generation tools. Instead, they are becoming an integral part of the modern software development lifecycle.

Kiro can support developers throughout multiple stages of software development.

## Requirements Analysis

Kiro helps transform vague ideas into well-defined software requirements.

For example, suppose you're building an **AI Meeting & Workforce Management Platform**.

Instead of simply asking AI to "build a meeting summarization feature," Kiro can help break the feature into clear functional requirements:

- Upload audio files or meeting transcripts.
- Convert audio into text.
- Generate meeting summaries.
- Extract action items from meeting content.
- Assign responsible team members.
- Identify deadlines.
- Save results for future review.
- Allow users to edit AI-generated tasks.

By defining these requirements first, developers gain a much clearer understanding of what the system is expected to accomplish before implementation begins.
## Technical Design

Once the requirements are clearly defined, Kiro can assist in generating a technical design, including recommendations for the frontend, backend, database, APIs, AI processing services, file-processing queues, and user authorization mechanisms.

However, this stage still requires human review. While AI can quickly propose an architecture, developers must evaluate whether it is appropriate for the project's size, complexity, and business requirements.

For student projects, there is little benefit in adopting an overly complex architecture. For enterprise systems, additional considerations such as security, logging, monitoring, cost optimization, and scalability become essential.

---

## Code Implementation by Tasks

Once the specification is finalized, Kiro can help implement individual tasks rather than generating an entire feature at once.

For example:

- Build the file upload interface.
- Develop the file upload API.
- Validate file format and size.
- Store metadata in the database.
- Invoke the transcript processing service.
- Extract tasks from meeting content.
- Display generated tasks on the dashboard.

Breaking implementation into smaller tasks makes code reviews easier and reduces the risk of AI modifying too many parts of the project simultaneously.

---

## Testing and Documentation

Another strength of Kiro is its ability to generate tests and documentation. These are often overlooked in student projects but are critical in professional software development.

Kiro can assist with:

- Writing test cases.
- Generating README documentation.
- Explaining application workflows.
- Producing API documentation.
- Updating documentation whenever features change.

Even so, developers should avoid relying entirely on AI-generated tests. Test cases should always be reviewed to ensure they accurately reflect the project's actual requirements.

---

# BENEFITS FOR STUDENTS AND DEVELOPMENT TEAMS

For students, Kiro is more than just a coding assistant—it also helps build better software engineering practices.

Some of its key benefits include:

- Learning how to analyze requirements before writing code.
- Understanding technical design principles.
- Breaking projects into manageable implementation tasks.
- Creating well-structured documentation for reports and presentations.
- Reducing the tendency to write code without proper planning.
- Simplifying the onboarding process for new team members.
- Developing the ability to review and evaluate AI-generated outputs.

For team projects in particular, having clear specifications and well-defined implementation tasks helps everyone share the same understanding of the project, reducing inconsistencies where each developer implements features differently.
# LIMITATIONS AND RISKS TO CONSIDER

Although Kiro is a promising AI coding assistant, it should not be considered a replacement for software developers.

There are several limitations and risks that users should keep in mind.

## AI May Misinterpret Requirements

If the initial prompt or specification is unclear, the generated requirements may also be inaccurate. As a result, the AI may produce code that appears correct but does not actually meet the intended business objectives.

---

## AI May Over-Engineer the Solution

For relatively simple features, AI may generate unnecessary files, introduce excessive abstractions, or create more test cases than needed. Instead of simplifying development, this can make the project more difficult to maintain.

---

## Code Review Is Still Essential

AI-generated code can still contain logical errors, security vulnerabilities, or architectural issues. Developers should always review, test, and validate AI-generated code before integrating it into a production environment.

---

## Monitor Cost and Resource Usage

Most AI development tools consume credits or incur usage-based costs. If requirements are unclear and multiple generations are required, unnecessary expenses can accumulate over time.

---

## Never Include Secrets in Prompts

Sensitive information such as API keys, access tokens, passwords, or confidential business data should never be included in prompts.

If the AI has permission to modify project files or execute commands, its scope should be carefully restricted, and all generated changes should be reviewed before being accepted.

---

# BEST PRACTICES FOR USING KIRO

Based on our experience, here are several recommendations for using Kiro more effectively:

- Start with a specification instead of generating code immediately.
- Always review and refine the requirements before implementation.
- Break large features into smaller tasks.
- Avoid allowing AI to modify too many parts of the project at once.
- Never expose sensitive information in prompts.
- Test the application after every significant change.
- Treat AI as a development assistant rather than the final decision-maker.
- In team projects, assign separate reviewers for specifications and generated code.

---

# CONCLUSION

Kiro is an impressive AI coding assistant from AWS, not only because of its code generation capabilities but also because it represents the growing trend of the **AI-assisted development lifecycle**.

Its greatest strength lies in encouraging developers to follow a structured software engineering process—starting with requirements analysis, moving through technical design and task planning, and continuing with implementation, testing, and documentation.

For students and project teams, Kiro is a valuable tool for learning professional software development practices. However, AI remains a supporting tool rather than a replacement for developers. Engineers are still responsible for understanding business requirements, reviewing AI-generated code, ensuring security, and maintaining overall software quality.

In our opinion, future software developers will not simply be people who write code. Instead, they will be professionals who can define clear requirements, collaborate effectively with AI agents, evaluate AI-generated outputs, and design reliable, scalable systems.

This is our first time researching and writing about Kiro. If you notice any inaccuracies or have additional insights, we would greatly appreciate your feedback.
# References

- AWS Documentation – Kiro Documentation  
  https://aws.amazon.com/documentation-overview/kiro/

- Kiro Blog – Introducing Kiro  
  https://kiro.dev/blog/introducing-kiro/

- Kiro Docs – Specs  
  https://kiro.dev/docs/specs/

- Kiro Docs – Steering  
  https://kiro.dev/docs/steering/

- Kiro Docs – Hooks  
  https://kiro.dev/docs/hooks/

- AWS Architecture Blog – Announcing the Updated AWS Well-Architected Machine Learning Lens

- AWS Security Blog – Five Ways to Use Kiro and Amazon Q to Strengthen Your Security Posture

![](/images/3-BlogsTranslated/Blog1-1.jpg)

![](/images/3-BlogsTranslated/Blog1-2.jpg)

![](/images/3-BlogsTranslated/Blog1-3.jpg)