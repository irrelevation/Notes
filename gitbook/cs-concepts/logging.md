# Logging

Things to keep in mind

- Remember the reader
- No sensitive data
- What is the **context**?
- What is the **purpose**?
  - Debugging
  - Analytics
- How **important** is the event?
- **Format**
  - human readable
  - `grep`able
  - scannable
  - parsable

## Types of Logging

| Name | Goal | Question | Content | Audience |
| --- | --- | --- | --- | --- |
| Tracing | Debugging | How'd we get here? | State Changes | Devs |
| Event | Analytics | What's happening? | Actions & Exceptions | Admins / Product Owners / Devs |
| Progress | UX | Are You OK? | Percentage / Errors | Users |
| Audit | Verification | Are You Lying? | Summaries, Double-entry book keeping | Compliance, Gov, Business |

## References

[Logging Best Practices](https://blog.appsignal.com/2021/09/01/best-practices-for-logging-in-nodejs.html)
