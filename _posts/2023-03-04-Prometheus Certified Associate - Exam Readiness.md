---
layout: post
title: Prometheus Certified Associate - Exam Readiness
share-img: /assets/img/PCA Preparation.png
thumbnail-img: /assets/img/PCA Preparation.png
tags: [Linux,Monitoring]
---
## Objective

The main objective of this post is to give information about how to study and pass PCA exam hosted by Linux Foundation. By reading this blog, you will have a quick insight about how to start studying for Prometheus in order to manage and analyze your application’s observability data and visualize that data into graphs. 

## **Domains & Competencies**

As per Linux Foundation, the **curriculum** for Prometheus Certification is described as follows:

📄 **Observability Concepts                   18%**

📄 **Prometheus Fundamentals            20%**

📄 **PromQL                                                28%**

📄 **Instrumentation and Exporters     16%**

📄 **Alerting & Dashboarding                18%**

## Learning Objectives

- I think the most important section in learning Prometheus is no other than **PromQL**.
- You can test around PromQL metrics in this [link]([https://demo.promlens.com](https://demo.promlens.com/)).
- You can learn about basic Prometheus system architecture [here]([https://prometheus.io/docs/introduction/overview/#architecture](https://prometheus.io/docs/introduction/overview/#architecture)).
- You can explore about Prometheus basic functions [here]([https://prometheus.io/docs/prometheus/latest/querying/functions](https://prometheus.io/docs/prometheus/latest/querying/functions/)).
- Learning AlertManager is also an important factor in learning about Prometheus. You can get an overview of AlertManger functionalities [here]([https://prometheus.io/docs/alerting/latest/alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/)).
- You can visualize your alertmanager routes in this [link]([https://prometheus.io/webtools/alerting/routing-tree-editor](https://prometheus.io/webtools/alerting/routing-tree-editor/)).
- Basic understanding of exporters such as node_exporter and blackbox_exporter is needed for PCA exam.
- In Prometheus, you can use two rules types for different purposes:
    - Record rules allow you to precompute frequently needed or computationally expensive expressions and save their results as a new set of time series.
    - Alert rules allow you to define alert conditions, using queries which are written in Prometheus Query Language (Prom QL) that are applied on Prometheus metrics and if a condition is met, alert is sent to AlertManager.
- Meta-monitoring is the concept of monitoring the monitoring instances itself like Prometheus.

## Exam Experience

My personal exam experience went very well, I believe. You can use your Linux Foundation training portal to check in 30 minutes before your appointment time. After you start the check-in procedure, you must install the PSI secure browser. Then, you must snap a photo of both you and your form of identification, such as a passport or driver's license. Then a live proctor will ask you to show around your desk, such as under the desk. You are not allowed to have any electronic devices or paper notes nearby. If you successfully completed check-in process, you are now ready to go. I advise against spending too much time considering a single question. If you believe you are unsure of the answer, you flag for review and then move on to the next question.

# Conclusion

In conclusion, my Prometheus exam experience was outstanding. I am thrilled to have passed the Prometheus Certified Associate certification and gained a deeper understanding of monitoring, alerting, and visualization using Prometheus.

The certification process was challenging, but it was also an excellent opportunity to expand my knowledge and skills in this field. I appreciate the rigor and thoroughness of the exam, which helped me to learn and grow in ways that will benefit me in my work.

# Resources Sharing

## Free Resources

You can explore and learn about PCA Certification and exam related topics free in these GitHub Repositories.

- [https://github.com/walidshaari/PrometheusCertifiedAssociate](https://github.com/walidshaari/PrometheusCertifiedAssociate)
- [https://github.com/edgarpf/prometheus-certified-associate](https://github.com/edgarpf/prometheus-certified-associate)
- [https://github.com/Al-HusseinHameedJasim/prometheus-certified-associate](https://github.com/Al-HusseinHameedJasim/prometheus-certified-associate)

## Paid Resources

I want to recommend some of the paid courses I took a watch in my journey to becoming a Prometheus Certified Associate.

- [https://kodekloud.com/courses/prometheus-certified-associate-pca](https://kodekloud.com/courses/prometheus-certified-associate-pca/)
- [https://www.udemy.com/course/prometheus-course](https://www.udemy.com/course/prometheus-course/)