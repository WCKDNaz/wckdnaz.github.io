# Personal Purpose
This page is created to reflect on my journey through the field of Information Technology and other disciplines such as Machine Learning and Artificial Intelligence.
I'll be continuously uploading my projects that I am working on, solutions of Capture The Flag (CTF) challenges from my own point of view, showcasing my methodology & knowledge.

<br>
<p align="center">
  <img src="https://tryhackme-badges.s3.amazonaws.com/WCKDNaz.png" alt="Static-THM-Badge" />
</p>

## Technical Skills:
Python | Unix CLI | OST | Bash | SQL | MATLAB | Machine Learning | C (Learning)

## Education
### M.Sc of Artificial Intelligence | University of East London, London (UEL) (_Jan 2024_) - (_Present_)
Major Disciplines:
-   Intelligent Systems
-   Big Data Analytics
-   Machine Learning
-   Machine Vision

### B.BA of Information Management | Arab Academy for Science, Technology, And Maritime Transport, Egypt (AASTMT) (_Sept 2017_) - (_Sept 2021_)
Major Disciplines:
-   Information System Analysis & Design
-   Website Development
-   Database Management
-   Networking

## Non-Credit Courses & Certificates:
[Machine Learning Onramp](https://matlabacademy.mathworks.com/progress/share/certificate.html?id=72c95f65-6b5f-433d-b0ab-b49c6db102eb&) |
[Image Processing Onramp](https://matlabacademy.mathworks.com/progress/share/certificate.html?id=9f28e5fd-4054-4c9b-a394-de9d31dccd36&) |
[Deep Learning Onramp](https://matlabacademy.mathworks.com/progress/share/certificate.html?id=048d77ec-0f25-4107-ac61-9dfa839756bc&) - **MathWorks**

[Cisco CyberOps (200-201) Assosciate Guide](https://www.udemy.com/certificate/UC-85d2e568-5c4f-4b08-9e8b-06cf7b091176/) - **Udemy**

[THM Advent of Cyber 2023](https://tryhackme-certificates.s3-eu-west-1.amazonaws.com/THM-ZLF36RUJWF.png) - **TryHackMe**

## Capstone Projects
### URL Binary Classification (Malicious or Benign) - Supervised ML
>Built a model from scratch using **pyspark's** framework to determine whether a URL is malicious or benign based on a set of carefully selected features.
>
>Features were identified by the output of a heatmap using **numpy's** and **sklearn's** libraries that correlated the highest impact of all viable columns to the target label column, and then aggregated by using `VectorAssembler` to be parsed in as one single feature vector.
>
>Utilized different learners to gain an initial model, furthermore gaining insight to build an approach to tackle the objective, utilized different methods such as aggregating the sum of two different learner outputs, modified `losstype` etc.
>
>Incorporated `ParamGridBuilder` and `CrossValidator` with `GBTClassifier`, added `weight` to respective labelled instances as a measure of balance in the dataset.
>
>Finally, a confusion matrix was utilized to measure the accuracy of the trained model's prediction on the given test set. **Achieved 91-92% Accuracy**

### Rice Seed MultiClass-Classification - CNN & Transfer Learning
>Built a neural network from scratch as part of my studies for my A.I - Machine Vision course. The network was relatively small in size and performed poorly.
>
>Later on, I decided on using a transfer learning approach to configure a pre-trained neural network that used `GoogleNet`'s network architechture.
>
>Configured `inputLayer` and `classificationLayer` respectively according to the number of classes existing in the dataset, set hyper-parameters to validate the learning process.
>
> Finally, utilized a confusion matrix using MATLAB to analyze the results of true-positives and false-negatives. **Achieved 94-95% Accuracy**

## CTF Machine Write-Ups
[Basic Pentest Room - THM](https://wckdnaz.medium.com/basic-pentesting-writeup-thm-4bb027c82a34)

## CTF Challenges & Module Walkthroughs
[PwnCollege - Module](./pwncol-walkthroughs/pwncol.md) |
[OverTheWire - Module](./overthewire-walkthroughs/otw.md) | 
[CryptoHack - Challenges](./cryptohack-walkthrough/challenges.md) | 
[PicoCTF - Challenges](./picoctf/pico-challenges.md)

## Socials & Public Profiles
[LinkedIn](https://www.linkedin.com/in/omar-nassar-b87277222/) |
[TryHackMe](https://tryhackme.com/p/WCKDNaz) |
[HackTheBox](https://ctf.hackthebox.com/user/profile/431133) |
[PwnCollege](https://pwn.college/hacker/wckdnaz)
