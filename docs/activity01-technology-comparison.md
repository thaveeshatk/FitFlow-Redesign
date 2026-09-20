Activity 1 – Evaluating Mobile Development Options

Overview

Choosing the right technology stack for rebuilding the FitFlow fitness app is a key early decision, since the app must run smoothly on iOS, Android and the web without sacrificing performance. On top of that, the redesigned app needs to support live workout tracking, push notifications, AI-driven exercise suggestions, secure sign-in, and constant syncing of user data across devices.
Four candidate technologies were reviewed for this purpose: Flutter, React Native, Kotlin Multiplatform, and Swift/SwiftUI.
Technology Comparison

Criteria	Flutter	React Native	Kotlin Multiplatform	Swift/SwiftUI
Build Speed	High: one codebase plus hot reload	High: fast iteration via Fast Refresh	Medium: logic is shared but platform UI often needs separate work	Medium: geared toward Apple platforms only
Code Sharing	Excellent: most UI and logic reused across platforms	Excellent: a large share of the codebase can be reused	Very high for business logic; UI sharing varies by approach	Low outside of Android/web
Runtime Performance	Very high: compiles down to native machine code	High: relies on native widgets but the JS bridge can add latency	Very high: shared Kotlin logic paired with native platform capability	Excellent: tightly optimised for Apple hardware
Ecosystem	Strong and expanding quickly	Very strong, backed by the JS/React community	Growing, though still smaller than Flutter or RN	Very strong inside the Apple ecosystem
Learning Curve	Moderate: Dart and the Flutter framework must be learned	Moderate: easier for developers already comfortable with JS/React	Moderate to steep: needs both Kotlin and native platform knowledge	Moderate: requires Swift and SwiftUI
Web Support	Good: Flutter can target the web directly	Good: React Native Web reuses components with some adjustment	Limited and still maturing versus Flutter/RN	Poor for a multi-platform web need
AI/ML Support	Good: APIs and native ML libraries are usable	Excellent: benefits from the wide JS ecosystem and native modules	Excellent: can tap into Kotlin/JVM and native integrations	Excellent: strong access to Apple's Core ML tooling
Live/Real-Time Features	Excellent via WebSockets, Firebase, etc.	Excellent, supported by Firebase, WebSockets and third-party libraries	Excellent through shared networking/business logic	Excellent via native networking support
Ongoing Maintenance Cost	Low: mostly a single codebase	Low to medium: shared code but some platform-specific upkeep	Medium: shared logic cuts duplication but platform code remains	High when multiple platforms must be supported
Security	Good: secure storage, auth and native security APIs available	Good: strong security libraries and native hooks	Very good: combines Kotlin and native platform security features	Excellent: strong Apple security ecosystem
Ideal Use Case	Cross-platform apps needing a uniform UI	Cross-platform apps built on React/JS	Shared logic with platform-native UI	High-end Apple-exclusive apps




Flutter
Flutter is Google's UI toolkit built around the Dart language, letting teams target Android, iOS, the web and beyond largely from one codebase.
Advantages
•	One codebase covers Android, iOS and web.
•	Hot Reload speeds up iteration during development.
•	Ships with a large set of customisable widgets.
•	Keeps the UI visually consistent across platforms.
•	Strong performance since apps compile natively instead of depending fully on a JS bridge.
•	Works with real-time tools such as WebSockets, Firebase and REST APIs.
•	AI/ML features can be added via APIs, plugins or native libraries.
•	Long-term upkeep is lighter because most of the code is shared.
Drawbacks
•	New developers must pick up Dart if they haven't used it before.
•	App size can end up larger than a fully native build.
•	Certain advanced platform features still need native Android/iOS code.
•	Web output may need extra tuning for web-specific needs.

React Native
React Native lets teams build mobile apps in JavaScript/TypeScript using React, making it a natural fit for developers coming from web development.
Advantages
•	A large share of code can be reused across Android and iOS.
•	Draws on the extensive JavaScript/TypeScript ecosystem.
•	Fast Refresh keeps development quick.
•	Backed by a large community and many third-party packages.
•	React Native Web extends it to the browser.
•	Integrates well with Firebase, WebSockets and general APIs.
•	AI/ML services can be reached through APIs or native modules.
•	Developers with React experience can pick it up quickly.
Drawbacks
•	Some advanced capabilities still require native Android/iOS code.
•	Quality and upkeep of third-party libraries varies.
•	Heavy processing or frequent JS-to-native calls can hurt performance.
•	Keeping libraries compatible across platforms adds maintenance work.

Kotlin Multiplatform
Kotlin Multiplatform (KMP) shares core application logic across platforms while still allowing native capability where it matters.
Advantages
•	Business logic can be shared between Android and iOS.
•	Strong performance since platform-specific code can run natively.
•	Kotlin has robust support for modern app development.
•	Direct access to native Android and iOS APIs.
•	Well suited where native UI and performance matter most.
•	Cuts duplication in networking, data handling and business rules.
Drawbacks
•	Smaller ecosystem than Flutter or React Native.
•	Developers need familiarity with both KMP and native platform work.
•	UI sharing is less seamless than Flutter's single-UI model, depending on setup.
•	Web support isn't as mature for this kind of requirement.
•	More platform-specific code raises overall complexity.

Swift/SwiftUI
Swift and SwiftUI are Apple's own tools for building apps on iOS and other Apple devices.
Advantages
•	Excellent performance on Apple hardware.
•	Tight integration with iOS hardware and system APIs.
•	Solid support for health, fitness and ML-related Apple frameworks.
•	Swift is a modern, type-safe language.
•	SwiftUI allows quick UI building for Apple platforms.
•	Strong security and platform integration.
Drawbacks
•	Locked mainly to the Apple ecosystem.
•	Android needs an entirely separate codebase and technology.
•	Not viable for FitFlow's need for a unified Android/iOS/web experience.
•	Cost of development and maintenance rises when supporting several platforms.
•	Non-Apple platforms would need their own separate solution.

Fit for FitFlow
FitFlow's requirements can be summarised as:
1.	Support for Android and iOS
2.	Accessibility on the web
3.	High-performance workout tracking
4.	Real-time data syncing
5.	AI/ML-driven recommendations
6.	Secure authentication and data storage
7.	Quick development turnaround
8.	Low ongoing maintenance
9.	A consistent UI/UX
10.	Room to scale in the future
Given these needs, Swift/SwiftUI falls short despite its performance, since FitFlow must also run on Android and the web.
Kotlin Multiplatform offers strong native performance and logic sharing, but the extra platform-specific work and its comparatively weaker web story make it a less complete fit for a three-platform product.
React Native is a solid contender thanks to its large ecosystem, TypeScript support, React Native Web, and good real-time/API capabilities, though native-module dependencies can add complexity for some advanced features.
Flutter offers the best overall balance for FitFlow, largely sharing one codebase across Android, iOS and web while still delivering strong performance and a consistent interface.

Recommendation
Recommended Technology: Flutter
Flutter is put forward as the primary technology for rebuilding FitFlow.
It is chosen mainly because it balances development speed, performance, code reuse, UI consistency and maintenance cost better than the alternatives.
Most of FitFlow can be built from a single Flutter codebase, cutting down on repeated work and simplifying upkeep across Android, iOS and web.
Flutter also fits the interactive feel a fitness app needs — workout animations, progress views, dashboards, timers and live updates can all be built with its UI and animation toolkit.
AI/ML capability can be layered on through backend services or native ML frameworks, while Firebase, REST APIs and WebSockets handle real-time sync, authentication, notifications and other cloud features.
Proposed Architecture
A workable setup for FitFlow would look like this:
Flutter + Dart
•	Cross-platform UI
•	Android app
•	iOS app
•	Web app
•	Workout tracking
•	Progress dashboards
•	Animations
Backend API
•	User management
•	Workout data
•	Nutrition data
•	Social features
•	AI/ML processing
Firebase / Cloud Services
•	Authentication
•	Push notifications
•	Real-time synchronisation
AI/ML Service
•	Personalised workout recommendations
•	Activity analysis
•	Nutrition recommendations
•	Fitness predictions
Native Integration where needed
•	Android-specific fitness/device APIs
•	iOS HealthKit and other Apple-only capabilities
This hybrid setup lets FitFlow benefit from cross-platform development while still reaching native features when it needs to.
Overall Conclusion
Taken together, Flutter is the best fit for rebuilding FitFlow, since the top priority is a consistent Android, iOS and web experience without maintaining separate codebases.
React Native would be the next-best pick, especially if the team already has strong JavaScript/TypeScript/React skills. Kotlin Multiplatform would suit a scenario where native performance and platform-specific UI matter more than maximum code sharing. Swift/SwiftUI would be excellent for an Apple-only app but doesn't fit FitFlow's cross-platform need.
The suggested path forward, then, is Flutter as the core cross-platform framework, backed by native integrations and backend AI/ML services as needed — giving a practical mix of performance, scalability, development speed, maintainability, security and cross-platform reach.
