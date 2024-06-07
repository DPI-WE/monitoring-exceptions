# Monitoring Your Application 🔍

## Introduction
Monitoring your application is crucial to ensuring its health, performance, and reliability. When your app is live, you need to track exceptions, monitor performance, and keep detailed logs to maintain a smooth user experience and quickly address any issues that arise.

In this lesson, we'll explore the tools and practices that help you monitor your Rails application effectively.

## Tracking and Managing Exceptions
When your application is running in production, tracking exceptions is vital to maintaining stability and providing a seamless user experience. Integrating tools like [Airbrake](https://www.airbrake.io/) or [Rollbar](https://rollbar.com/) into your application helps you manage and respond to errors efficiently.

Benefits of Using Exception Tracking Tools:
- **Catching Exceptions**: These tools automatically catch and log errors that occur in real-time, providing immediate visibility into issues.
- **Notification**: Get notified immediately when an exception occurs, allowing for quick responses to critical problems.
- **Debugging Assistance**: Detailed reports and contextual information help you track down and resolve issues quickly, minimizing downtime and improving user experience.

![](/assets/airbake-error.png)

## Performance Monitoring
Monitoring the performance of your application is essential to ensure it can handle load efficiently and provide a fast user experience. Tools like [New Relic](https://newrelic.com/ruby/rails) and [Render's built-in metrics](https://docs.render.com/service-metrics) provide valuable insights into your application's performance.

Key Metrics to Monitor:
- **Memory Usage**: Track how much memory your application uses and identify any memory leaks or inefficiencies.
- **CPU Usage**: Monitor the CPU usage to ensure your application is running efficiently and identify any processes that consume excessive CPU resources.
- **Disk Usage**: Keep an eye on disk usage to prevent running out of space, which could lead to performance degradation or downtime.
- **HTTP Request Metrics**: Analyze request volume, response latency, and outbound bandwidth to understand how your application handles traffic and how quickly it responds to user requests.

You can set up performance monitoring on Render by following their service metrics documentation.

![](/assets/metrics-ram.webp)

![](/assets/metrics-response-times.webp)

## Keeping Logs
Logging is a fundamental aspect of monitoring that provides insights into your application's behavior and helps troubleshoot issues.

Benefits of Effective Logging:
- **Historical Insights**: Logs provide a historical record of events, which is invaluable for diagnosing issues and understanding application behavior over time.
- **Debugging**: Detailed logs help pinpoint the source of errors and unexpected behavior.
- **Auditing**: Logs can be used for auditing user actions and system events, which is crucial for security and compliance.

### Best Practices for Logging:
- **Log Important Events**: Log significant actions, errors, and state changes in your application.
- **Use Log Levels**: Employ different log levels (e.g., debug, info, warn, error) to categorize logs based on their severity and importance.
- **Centralize Logs**: Use tools like [Papertrail](https://www.papertrail.com/plans/) to centralize and analyze logs from multiple sources.

Here’s an example of adding logging to a Rails controller:

```ruby
class OrdersController < ApplicationController
  def create
    @order = Order.new(order_params)
    if @order.save
      Rails.logger.info("Order created successfully: #{@order.id}")
      redirect_to @order
    else
      Rails.logger.error("Order creation failed: #{order_params}")
      render :new
    end
  end
end
```

## Quiz

- What is the primary purpose of integrating tools like Airbrake or Rollbar into your Rails application?
- To monitor CPU usage.
  - Not quite. Airbrake and Rollbar are primarily used for tracking and managing exceptions.
- To track and manage exceptions.
  - Correct! These tools help catch and log errors in real-time, providing detailed reports for debugging.
- To store logs for auditing purposes.
  - Not quite. While these tools can provide insights into errors, they are specifically designed for exception tracking rather than general logging.
{: .choose_best #exception_tracking title="Purpose of Exception Tracking Tools" points="1" answer="2" }

- Which of the following metrics is NOT typically monitored by performance monitoring tools?
- Memory Usage
  - Not quite. Memory usage is a critical metric monitored by performance tools.
- HTTP Request Metrics
  - Not quite. HTTP request metrics are essential for understanding how your application handles traffic.
- User Interface Design
  - Correct! Performance monitoring tools focus on technical metrics like memory and CPU usage, not on UI design.
{: .choose_best #performance_metrics title="Metrics Monitored by Performance Tools" points="1" answer="3" }

- Why is logging important in application monitoring?
- It helps track user behavior and system events over time.
  - Correct! Logging provides a historical record of events, aiding in debugging and understanding application behavior.
- It replaces the need for performance monitoring.
  - Not quite. Logging complements performance monitoring but does not replace it.
- It ensures application code is error-free.
  - Not quite. While logging helps identify errors, it doesn’t ensure the code is error-free.
{: .choose_best #logging_importance title="Importance of Logging" points="1" answer="1" }

- What is a key benefit of using centralized logging tools like Papertrail?
- They allow monitoring of CPU usage.
  - Not quite. While useful for performance data, these tools are specifically designed for centralized logging and log analysis.
- They provide detailed analytics and search capabilities for logs.
  - Correct! Centralized logging tools help aggregate logs from various sources and provide powerful analytics and search functionalities.
- They automate the deployment process.
  - Not quite. Centralized logging tools focus on log management, not deployment automation.
{: .choose_best #centralized_logging title="Benefit of Centralized Logging Tools" points="1" answer="2" }

## Conclusion
Effective monitoring of your application through exception tracking, performance monitoring, and logging is essential for maintaining a robust and reliable system. These practices enable you to catch and resolve issues quickly, ensuring a smooth and uninterrupted user experience.

Remember, staying proactive with monitoring tools and practices helps you stay ahead of potential problems. Happy monitoring! 🔍
