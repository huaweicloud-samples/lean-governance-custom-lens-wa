# SaaS 多租户检查单 架构评估检查单

> 架构评估检查单（Well-Architected 最佳实践检查项的华为云语境转写）
>
> 题目语义与原最佳实践检查项一致，服务名已映射为华为云对应服务。

**华为云对应**：SaaS 多租户检查单（SaaS 架构评估）

## 评估说明

按三档自评：**良好 / 部分符合 / 不符合**；每个问题对照「期望回答与改进计划」给出行动项。

## GEN — General（3 题）

### gen1 GEN 1 Identify your company profile

说明：Not all companies fit perfectly into one category and your company can be a blend of a few profiles. The following is a list of hypothetical profiles that represent the typical starting points for companies moving to SaaS.

期望回答（参考）：
- Toe Dipper (T) - Transforming existing product with paced time-to-market
- Survivor Tech (S) - Transforming existing product with urgent time-to-market
- Unicorn (U) - New product with urgent time-to-market
- New Horizon (N) - New product with paced time-to-market

### gen2 GEN 2 How much experience do you have building and operating SaaS within your organization today?

说明：Gauge your familiarity with SaaS concepts, development, and operations. This allows you to be prepared and providing necessary supports to maximize the chances of success.

期望回答（参考）：
- Expert level experience across the organization
- Advanced experience in both business and technical areas
- Mixed experience, some strengths and some gaps in both business and technology areas
- Mixed experience, strengths in business areas but gaps in technology areas
- Mixed experience, strengths in technology areas but gaps in business areas
- Low or no experience in both business and technology areas

### gen3 GEN 3 Who are the key stakeholders and executive sponsor currently involved in your SaaS initiative?

说明：Different key participants should involve in different phases. For example, in the planning phase, you may feel only the executives, product managers and financial leaders are the best candidates, but technical and operations teams will also have important insights that can guide how you look at tiering the offering for different customer segments. Each key area of your company should be included in this exercise.

期望回答（参考）：
- Executive Leadership 
- Marketing / Sales
- Finance
- Product Management
- Development / Engineering
- Operation
- Customer Success
- Customer Support
- Others

---

## PHASE1 — Phase 1 Business Planning（7 题）

### plan1 PLAN 1 Assess the SaaS Opportunity

说明：Determine if the SaaS delivery model is well-aligned with customer needs and market dynamics. Assess whether this is a valid opportunity and define the vision for what you are targeting with your SaaS offering. Suggested participants: Executives, product managers and financial leaders. Also Technical and operational teams.

期望回答（参考）：
- What are your compelling factors for adopting SaaS?
- How many of your existing customers are expected to adopt your SaaS offering?
- Are SaaS competitors encroaching on your market?
- Are there new segments of the market that are best targeted by a SaaS offering?
- How long will it take your company to complete the transition to a SaaS model?
- What is the risk of not pursuing the SaaS initiative?
- Do you have a time-bound plan to launch the solution for General Availability?

### plan2 PLAN 2 Define Target Segments

说明：Create a profile of the different types of customers about your potential buyers. Likely to come out a list of the target segments accompanied by a breakdown of the experience, resource utilization, and value proposition for each segment.

期望回答（参考）：
- What are the customer segments that you are targeting?
- Are there any specific operational, performance, or compliance profiles of the different customers in this market?
- Will this offering be available to all customers or limited to new customers?
- Tell us about your customers, who are the buyers and users?
- How many customers do you intend to acquire in year-one of General Availability?

### plan3 PLAN 3 Evaluate the Market and Customer Strategy

说明：Define your approach to market and sell your SaaS offering to new customers and the incremental staffing or resource utilization that might be associated with taking your new offering to market.

期望回答（参考）：
- What channels will be used to access new customers?
- How will you differentiate your offering from competitors?

### plan4 PLAN 4 Model Market / Segment Growth

说明：Create projections over a 1-2-year window for your customer growth for each of the target customer segments.

期望回答（参考）：
- What data do you have to validate market acceptance and readiness for this offering?
- How many customers do you expect to add in the first year?
- How many existing customers do you expect to move into the new model?

### plan5 PLAN 5 Finance

说明：Develop a target monetization model for the customer segments, project the target revenue, growth, and retention for each of your segments.

期望回答（参考）：
- What is the monetization model for the new offering?
- What is the target MRR for this offering (across segments)?
- What would the charging rate need to be (for each segment) to be competitive?
- What is your projected cash flow (for the first year) after launching your SaaS offering?

### plan6 PLAN 6 Sales and Marketing Transformation

说明：Define new guidlines and compensation programs since the resources will be transitioned into SaaS roles. For sales, develop a profile for the transformation and determine the incremental resource utilization potentially associated with these changes. For marketing, develop a strategy to build a brand for your SaaS offering and a profile for the marketing company.

期望回答（参考）：
- What is different about selling SaaS?
- How will your sales organization need to transform to support a SaaS model?
- What resource utilization will be associated with sales activities to these customers?
- Do sales teams have the skills that align with a SaaS delivery model?
- How will you build a brand for your SaaS offering?
- What resource utilization will be associated with marketing activities to these customers?

### plan7 PLAN 7 Define Operational / Staffing Resources

说明：Identify any incremental resource utilization associated with operations footprints for you SaaS business. Also assess the business and technical skills of your team and develop a training or hiring plan to fill in any skill or industry gaps.

期望回答（参考）：
- What incremental expenses would be required to support this model?
- What is the Huawei Cloud charging model for operating the system (resource utilization per tenant)?
- Will new staffing resources be required to build/manage your DevOps pipeline?
- Will new development resources for this effort?
- What resource utilization are associated with staffing and hosting this solution?
- Do you have enough SaaS expertise to build the SaaS solution?
- Do you have the right development and operational tools to develop, test, and deploy SaaS?

---

## PHASE2 — Phase 2 Product Strategy and Roadmap（7 题）

### rmap1 ROADMAP 1 Developing user and buyer personas

说明：You should come out a strategy that goes beyond the first deliverable (at all the elements eg. onboarding experience, security, agility...etc) without going as far as creating a multi-year plan. A key component of this effort is a clear picture of the target customers and market. Suggested participants: Product managers will be at the center of the effort. Technical and operational teams. Sales and marketing.

期望回答（参考）：
- What key attributes would distinguish the different types of customers that would use your product?
- What is the range of market segments (e.g. entry level, mid-tier, enterprise) are you targeting with this offering?
- How do the needs and expectations each of these customer profiles change based on their segment?
- Is the user persona different than the buyer persona?
- Are there ways you need to differentiate the personas from the ones that are currently being targeted by your other offerings?

### rmap2 ROADMAP 2 Collecting Customer Data

说明：Collect data from target customers to get better insights into their product and service requirements. The goal here is to not rely purely on instinct or legacy insights, and focus on directly engaging your customers to assess their view, interests and expectations for a SaaS offering in your domain.

期望回答（参考）：
- How can you identify and reach customers you may not engage today?
- What are the key areas you want to target for collecting data, have you considered conducting a survey?
- What mechanism can you use to gather input from your potential customers?

### rmap3 ROADMAP 3 Defining Onboarding Experience

说明：A mapping of the onboarding experience that identifies the business, operational, system, and accounting constructs that must be configured and launched to introduce a new tenant into your system. Determine if this mechanism will be engaged directly by customers and/or some internally triggered process.

期望回答（参考）：
- How will customers sign up for your service?
- How frequently do you expect new customers to be onboarding to your system?
- For an internal process, what internal mechanisms will need to be automated to reduce friction in your onboarding process?
- Will you support a demo mode for your product that enables customer to run a trial experience?
- How will you capture metrics and data that will enable you to assess the efficiency of your onboarding flow?

### rmap4 ROADMAP 4 Profiling Security, Compliance, Geographic and Data Protection Requirements

说明：You not only need to know what these requirements are, but how they might vary from one type of customer to the other. Determine how these considerations might influence the way you build, eg. how you approach the multi-tenant aspects.

期望回答（参考）：
- Do your customers have specific compliance, geographic, or regulatory requirements that will influence the SaaS application?
- Are the regulatory and compliance requirements constrained specific areas of your application, or is this a global requirement?
- What is motivating your need for geographic reach (market segments, performance, compliance, availability, etc.)?
- How are your potential competitors addressing these requirements, how will you do?
- How will addressing these requirements effect the resource utilization and operational efficiency of your offering?
- How will onboarding be supported if you plan a multi-geography model?
- Can you offer more dedicated standalone solutions to customers that are less willing to operate in a shared infra model?
- Do you need to factor these considerations into your initial release or can this come later in your product lifecycle?
- Has your company outlined a specific GDPR policy that defines your general requirements and addressing the compliance of GDPR?
- What is the profile of your data and are there specific types of data that will require a greater level of isolation?

### rmap5 ROADMAP 5 Defining Agility Goals

说明：A clear description of the tenets and metrics that your company will be targeting as it builds out the operational, company, and business footprint of your SaaS environment. Define specific metrics that will assess cycle time, up time, and a host of other well-defined metrics that are used to assess SaaS agility.

期望回答（参考）：
- Are there specific agility goals you are targeting for your SaaS business?
- What metrics and tooling will you put in place to bring broad visibility and measurability to your agility goals?
- Which structural and cultural changes will be needed in your company to promote and prioritize agility?

### rmap6 ROADMAP 6 Developing a Packaging / charging Profile

说明：Understanding common monetization mechanisms and design a well-defined charging strategy that aligns with market expectations and customer value perception. This also helps you better achieve financial forecasting and resource allocation.

期望回答（参考）：
- What are the common mechanisms that are used to monetize solutions in your domain/market?
- Will your domain support a subscription-based charging model, if so, what unit(s) of consumption best for your target customers?
- Will you use features as a way to distinguish different tiers of your offering?
- What data can you use to identify the boundaries that will be most effective at distinguishing tenant tiers?
- Will you need to support a separate tier for high-value tenants that impose unique demands on your solution?

### rmap7 ROADMAP 7 Portfolio Management

说明：Optimize resource allocation across your product portfolio and align the product mix with your business strategy if you have multiple offerings in your portfolio.

期望回答（参考）：
- How can you evaluate the performance and identify the risks and opportunities of each product?
- Which high-value products should be prioritized?
- How resources should be allocated across the portfolio?

---

## PHASE3 — PHASE 3 Minimum Viable Service (MVS)（5 题）

### mvs1 MVS 1 Defining the Target Early Adopters for the MVS release

说明：Define an MVS release with clear definition and expectations. Suggested participants: Product teams and PM. Leadership team also plays a key role to ensure the delivery reaching the promised state.

期望回答（参考）：
- Which customer personas (from the broader list of personas) are you targeting with this solution?
- Will you be supporting a product tiered model and which tiers will be included in this MVS experience?
- Are there enough customers in this target set of personas to drive the adoption you will need to drive the platform forward?
- Are there concerns about how this offering will be positioned against any other offerings that might be in your portfolio?
- Are there clear boundaries between the offerings that can limit any confusion for the market?

### mvs2 MVS 2 Outlining the Minimum Product Functionality

说明：Based on the tiers/personas you target, capture high-level notions of key product features you will need to include for this offering.

期望回答（参考）：
- What are the primary product features of this SaaS service offering?
- Which features (if any) will be used to draw clear boundaries between personas/tiers?
- Will customers impose any specific requirements around security and data protection?
- What will be the registration process for introducing new tenants into the system?
- Will you offer a demo or free trial version of your product?
- Do both delivery and business teams understand and are aligned with what you are planning to deliver?

### mvs3 MVS 3 Outlining the Minimum Operational Experience

说明：Define a well-defined view of the operational experience that includes tooling, processes, and insights that will be needed to support this new environment. The emphasis here is on automating and streamlining the operational experience to lay the foundation for rapid innovation, agility, and market response.

期望回答（参考）：
- What are the non-functional attributes of the service offering?
- What are the metrics (if any) will you be collecting to gather insights into the consumption and activity of your customers?
- Are you expecting to have a zero-downtime policy for this service?
- What strategy or mechanisms will be in place to modernize changes to data representation without incurring downtime?
- What tools and processes will be used by your operational team to proactively detect and manage tenant issues?
- How will customer report issues? Will this be an interactive experience?

### mvs4 MVS 4 Target Feedback Experience

说明：Determine how you will (if you plan to) incorporate potential customers into your MVS development lifecycle. Capture their feedbacks on your MVS.

期望回答（参考）：
- What data will be used to assess the customer's perspective on this new service offering?
- Will targeted customers be enabled to provide feedback during the development process?
- Will you be able to engage customers from segments you may not target today?

### mvs5 MVS 5 Defining Core SaaS Tenets for the MVS

说明：Define a list of the tenets that outline precisely which goals you are targeting for the business, operational, and agility attributes of this minimum viable service. The challenge here is to have your sights on general SaaS best practices while still recognizing that you may not target the longer-term experience for this MVS. Being clear about this is essential to defining where the bar is.

期望回答（参考）：
- What near-term trade-offs will be made to get to market at a faster pace?
- How will these trade-offs impact the customer experience and long-term viability of your solution?

---

## PHASE4 — PHASE 4 Launch/GTM Strategy（7 题）

### gtm1 GTM1 Update customer journey maps

说明：Define a GTM strategy to measure whether customers are adopting the product and realizing its value. Suggested participants: Leaders from sales, marketing, customer success and finance.

期望回答（参考）：
- What assumptions made during earlier phases (Phase2&3) about buyer and user behaviors have been validated or debunked?
- How does Sales interact with Customer Success to ensure effective onboarding?
- As above, what are the team-level responsibilities during each stage of the customer acquisition process?
- What are the measurable indicators that tell you if a customer is using the product efficiently when onboarding?
- What attributes are common to your customers who struggled to realize value during the MVS phase?
- What company skill gaps do you need to address (train, outsource, hire) prior to launch?

### gtm2 GTM2 Establish commercial and operational frameworks for new customer acquisition

说明：Determine the skills, structure and processes required to efficiently acquire and stand new customers up, and align these requirements with a charging model.

期望回答（参考）：
- What is the customer acquisition (revenue) target for your first year in-market and What is your year-one margin expectations?
- How many new customers do you need to onboard (per tier) on an annual, quarterly, monthly basis, to meet your revenue target?
- How much will it resource utilization you to onboard these customers?
- What is the budget for CAC(customer acquisition resource utilization), inclusive of comprehensive sales and marketing resource utilization?
- How long will it take to recover CAC for a new customer?
- How much flexibility do you have with your discount strategy?
- How and when will you deprecate the legacy solution, how will you structure revenue quotas for the legacy model as its sunsets?
- Do your investors and executive leaders understand the economic ramifications of transforming to a SaaS model?

### gtm3 GTM3 Set customer retention and expansion objectives

说明：Forecast retained revenue (net of churn) and expansion revenue (up-sell, cross-sell). Set budgets for funding customer expansion resource utilization (CEC) and customer retention resource utilization (CRC).  Forecast customer lifetime value (CLTV) to include plans for customer retention and growth, over time.

期望回答（参考）：
- What is an acceptable annual churn (or retained revenue) and expansion revenue (up-sell, cross-sell)?
- What are your CEC(customer expansion resource utilization) and CRC(customer retention resource utilization) budgets?
- Are you migrating customers to SaaS from an on-premises legacy solution, when and what are the economic impacts?

### gtm4 GTM4 Determine appropriate Sales motions and compensation incentives

说明：Determine a relevant distribution model for new customer acquisition, typically some combination of pre-sales, inside sales, field sales, and partner/channel sales resources. Build sales motions (e.g. acquire, renew, expand) that qualify opportunities with rigor and align appropriate sales processes with offer complexity.

期望回答（参考）：
- How many sales representatives can you dedicate to the SaaS model given CAC budgets?
- What information do you need to discover during the pre-sales process to qualify likely-to-succeed prospects?
- Who will own renewals and expansion revenue quotas?
- How complex are your negotiations, do they require a high-touch consultative approach, can you simplify the process?
- Are your sales teams able to articulate competitive value proposition which underpin your charging and services?
- What is your strategy to land a customer, and expand the relationship?
- What role will channel partners play in your sales model?
- What compensation incentives can you offer our Sales representatives to reward product adoption and retention?

### gtm5 GTM5 Establish Marketing operations

说明：Plan marketing operations to span the entire customer lifecycle, covering new customer acquisition and expansion opportunities. You should leverage an account-based marketing (ABM) framework and/or in-product marketing resources to trigger low-friction, point-in-time campaigns, targeted to specific industry firmographics, buyer personas, and user patterns.

期望回答（参考）：
- What are the demand generation, lead generation, customer conversion funnel ratios you need to achieve for year-one?
- What technology can you introduce to make lead qualification and lead scoring processes efficient?
- Can you publish content (videos, user manuals, blogs, FAQs) to educate customers and reduce friction during the sales process?
- What focus groups should you use to analyze the effectiveness and profitability of your marketing campaigns?

### gtm6 GTM6 Define Customer Success (CS) charter and services

说明：Typically adoption or renewal, less-commonly, expansion, and a handshake process between sales and CS, preceding the onboarding of new customer. CS teams should create success plans aligned with desirable customer outcomes.

期望回答（参考）：
- What is the primary aim for the CS team?
- Can you monetize the CS team by selling it as a premium service?
- Who owns the customer relationship with the deciding party, during renewal?
- Will you align CS representatives with customers based on tier, industry or vertical expertise?
- How many customers can each CS representative manage effectively on an annual basis?

### gtm7 GTM7 Launch and Product Communication Strategy

说明：Define the scope of your product updates and its impact on your customers, including metrics that will help you measure effectiveness and ongoing improvements of your communications plan.

期望回答（参考）：
- What is important for your target audience, what type of information do they need or expect from you?
- Do some of your customers need additional support to communicate the product updates and train their employees?
- What should be the timing of this communication, how much time do your customers need to adopt new features/releases?
- Do you have a mechanism for your customers to provide feedback about product communications and suggest new features?
- What are the most important metrics to measure reach, engagement, and adoption?

---


*检查项合计：29 题*
