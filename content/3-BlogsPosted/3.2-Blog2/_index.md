---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# CONVERT VIEWERS INTO PLAYERS WITH AMAZON GAMELIFT STREAMS

Today I'd like to share how AWS solves the "Interactive Streaming" problem – transforming passive game streaming experiences into real-time, two-way interaction.

In game development, organizing playtests often takes a lot of time (loading builds, setup, video reviews). Simultaneously, interacting with the viewing community is also a barrier when viewers can only passively type in chat. To solve this problem, AWS has introduced a powerful hybrid architecture.

**3 "PILLARS" OF THE SOLUTION ARCHITECTURE:**

* **Amazon GameLift Streams:** Supports live game streaming from the server to the browser (WebRTC) with extremely low latency, achieving up to 1080p at 60 FPS without requiring players to download or install the game.

* **Amazon IVS (Interactive Video Service):** Receives gameplay streams and distributes them globally with subsecond latency.

* **AWS AppSync:** Acts as a bridge, providing WebSocket APIs to instantly transmit messages, reactions, and control commands from the audience back into the game.

**HOW DOES ARCHITECTURE FLOW WORK?**

1. Users interact with the React Frontend interface, securely authenticated through Amazon Cognito.

2. Amazon API Gateway and AWS Lambda are responsible for communication and initiating the stream session.

3. On the server side, GameLift Streams runs the game and simultaneously launches a background process called "Broadcast Sidecar".

4. This Sidecar application captures video/audio, encodes video using H.264, and pushes the stream directly to the Amazon IVS stage with a latency of less than 300ms.

**TECHNICAL HIGHLIGHTS: "CONTROL HANDOFF" MECHANISM**

The most impressive aspect of this solution is how it handles "control handoff" for participants. The system leverages the AWS AppSync Event API to coordinate state control messages very clearly, for example:

* TAKEOVER_REQUEST: Requests control from the current player.

* TAKEOVER_APPROVED: Approves and begins sharing the session via the CreateStreamSessionConnection API.

**SUMMARY**

This architecture not only optimizes the internal playtesting process of studios but also opens up enormous potential for media campaigns: where stream viewers can directly participate in the game (e.g., vote on direction, spawn monsters) right in their browser without experiencing lag.

![](/images/3-BlogsPosted/2/img/1.png)

![](/images/3-BlogsPosted/2/img/2.png)

![](/images/3-BlogsPosted/2/img/3.png)

**Link:** https://aws.amazon.com/blogs/gametech/creating-interactive-gaming-experiences-with-amazon-gamelift-streams-and-amazon-interactive-video-service/