# Expo Linking API Cold Start Deep Link Issue

This repository demonstrates a bug in the Expo `Linking` API where the `Linking.addEventListener` method may fail to trigger when the app is launched from a cold start and a deep link is opened at the same time.  The issue is intermittent and difficult to reliably reproduce, but this example shows a setup designed to highlight the problem.

## Reproducing the Issue

1. Clone this repository and run the project using Expo Go.
2. Completely close the app (don't just switch away).
3. Open a deep link (e.g. `exp://your-app-id.exponent.io/deeplink`).
4. Observe if the `Linking.addEventListener` callback is triggered.  You might need to repeat this process multiple times to see inconsistent behavior. 

## Solution

The provided solution utilizes a strategy of checking for initial deep links when the application starts and falling back to the event listener for subsequent deep links. This ensures handling of deep links even if the initial event listener misses the event.