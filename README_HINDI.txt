स्वच्छ सुल्तानपुर Android APK - GPS WebView Permission वाला प्रोजेक्ट
====================================================================

यह Native Android WebView ऐप आपके मौजूदा Google Apps Script वेब ऐप को खोलता है।
Google Apps Script URL, Google Sheet/Drive backend, PIN login, Dashboard, रिपोर्ट,
फोटो अपलोड और मौजूदा वेब ऐप के फीचर यथावत रखे गए हैं।

इस संस्करण में Android WebView के GPS permission flow को स्पष्ट रूप से संभाला गया है:
- Android Manifest में Fine और Coarse Location permissions
- WebView में setGeolocationEnabled(true)
- WebChromeClient.onGeolocationPermissionsShowPrompt()
- पहले Android runtime permission, फिर WebView origin permission
- Google Apps Script के HTTPS origins तक geolocation request सीमित

प्रोजेक्ट जानकारी
-----------------
Package: in.gov.swachsultanpur.app
Minimum Android: 6.0 (API 23)
Target Android: 12L (API 32)
Android Gradle Plugin: 8.2.2
Gradle: 8.2
Java: 17
Build output: app/build/outputs/apk/debug/app-debug.apk

महत्वपूर्ण
----------
1. यह SOURCE PROJECT है, तैयार APK नहीं। APK GitHub Actions पर बनेगा।
2. MainActivity.java में APP_URL वही मौजूदा Apps Script URL है। इसे बिना जरूरत न बदलें।
3. Apps Script deployment URL मोबाइल Chrome में HTTPS पर खुलना चाहिए।
4. GPS चलाने के लिए फोन की मुख्य Location setting भी ON होनी चाहिए।
5. पहली बार GPS दबाने पर Android permission dialog आएगा। Allow चुनें।
6. यदि user Approximate location चुनता है, तो स्थान कम सटीक हो सकता है।
7. यह online-first ऐप है; इंटरनेट आवश्यक है।
8. Debug APK परीक्षण के लिए है। Play Store release के लिए अलग signing और policy review चाहिए।

Windows 7 कंप्यूटर से APK बनाने का तरीका (GitHub Actions)
--------------------------------------------------------
Android Studio install करने की जरूरत नहीं। Build GitHub के cloud runner पर होगा।

1. GitHub पर अपना repository खोलें: SwachhGram-Android-App
2. इस ZIP को Extract करें।
3. Extract किए हुए folder के अंदर की सभी files/folders repository के root में upload करें।
   ध्यान दें: .github/workflows/build-apk.yml भी upload होना चाहिए।
4. यदि GitHub पूछे तो पुराने समान project files को नई files से replace करें।
5. Commit changes करें।
6. Repository के Actions tab में “Build Swachh Sultanpur APK” खोलें।
7. Run workflow दबाएँ (या push के बाद अपने-आप शुरू हुए run को खोलें)।
8. Build सफल होने पर Summary के Artifacts में “Swachh-Sultanpur-debug-apk” डाउनलोड करें।
9. डाउनलोड ZIP extract करें। app-debug.apk फोन में भेजकर install करें।
10. पहले से installed पुराने APK को हटाने की जरूरत सामान्यतः नहीं; package name समान रखा गया है।
    यदि Android signature conflict बताए तो पुराना test APK uninstall करके नया install करें।

फोन पर GPS टेस्ट
----------------
1. फोन Settings में Location ON करें।
2. नए Swachh Sultanpur ऐप को खोलें और PIN से login करें।
3. फोटो अपलोड tab में “GPS लोकेशन प्राप्त करें” दबाएँ।
4. Android dialog में Location permission Allow करें।
5. GPS text में Latitude, Longitude और Accuracy आनी चाहिए।
6. Camera और Gallery दोनों टेस्ट करें; एक फोटो अपलोड करके Sheet/Drive रिकॉर्ड भी जाँचें।

यदि GPS फिर भी न चले
--------------------
- ऐप की Settings > Permissions में Location Allow देखें।
- Chrome में वही Apps Script URL खोलकर GPS टेस्ट करें।
- फोन में Google Location Accuracy / Location Services चालू रखें।
- खुले स्थान पर दोबारा प्रयास करें।
- Actions build log में error हो तो उसका पूरा screenshot भेजें।

सुरक्षा
-------
PIN को public repository या खुले WhatsApp group में न रखें।
यह PIN आधारित विभागीय उपयोग ऐप है; उपयोग से पहले संबंधित विभाग की स्वीकृति और
सुरक्षा समीक्षा कराएँ।
