# ✨ AWS Budget Setup Guide

> **Purpose:** This guide explains how to set up a monthly AWS cost budget with email alerts to help you stay within your planned cloud spending. In this case, we will configure a $20/month budget.

---

## 🔢 Step-by-Step Budget Creation

### 1. Go to AWS Budgets
- Log in to your AWS account.
- Open the **AWS Console**, and search for **"Budgets"**.
- Choose **Billing and Cost Management > Budgets**.

---

### 2. Create a New Budget
- Click **Create budget**.
- Select **"Cost budget"** as the budget type.
- Click **Next**.

---

### 3. Budget Details
- **Name**: `Monthly Budget - $20`
- **Period**: `Monthly`
- **Budget Type**: `Fixed`
- **Amount**: `$20.00`
- Click **Next**.

---

### 4. Configure Alerts
- Add an **Alert threshold** at `80%` of $20 (i.e., `$16.00`)
- Optionally, add another at `100%` (i.e., `$20.00`)
- Choose **"Actual cost"** for tracking
- Add your **email address** to receive alerts (you'll need to confirm it)

---

### 5. Review and Create
- Confirm all budget settings
- Click **Create Budget**

---

## 💼 Best Practices
- ✅ Set up alerts at both 80% and 100% thresholds.
- ✅ Monitor your usage in **Cost Explorer**.
- ✅ Use Free Tier eligible services where possible.
- ✅ Revisit your budget monthly and adjust if needed.

---

## 📅 Example Use Case
This budget setup is included as part of the broader `aws-infrastructure-setup` project to demonstrate financial governance for cloud resources. It's ideal for:
- AWS re/Start students
- Developers learning cloud on a budget
- Portfolio or sandbox environments

---

## 🔗 Resources
- [AWS Budgets Documentation](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)
- [AWS Free Tier](https://aws.amazon.com/free/)

> ✅ This guide is part of the [AWS Infrastructure Setup Project](https://github.com/At-Maag/aws-infrastructure-setup)
