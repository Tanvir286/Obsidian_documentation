![[next012.png]]

![[next015.png]]

## 📰 SSG(Static Site Generation)

যখন কোনো Project কে Deploy করি,তখন কিন্তু পুরো Project Build  করে নিতে হয়। Next js তাদের Project গুলোর Static Content কে Bundle করে Html File তৈরি করে। যা Build Time এ Create করে Html file গুলো যখন কোনো route৷ হিট করে,তখন তার deploy করা static file গুলো সব প্রথম visible হয়। সবগুলো static কোনো dynamic  content থাকবে না।

## 📰 SSR(Server Site Rendering)

User কোনো কিছুর জন্য Request করল,Request অনুসারে Database থেকে Query করে  Data নিয়ে এসে সে তার Html Content Create হয়,এবং Server থেকে Brower visible হয়ে থাকে। যা আগে থেকে তৈরি করা নেই ।