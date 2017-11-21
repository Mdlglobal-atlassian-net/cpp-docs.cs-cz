---
title: "Základy internetového programování MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a0c436a7fc1b7d567ed6cc684e76b46628de97d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-internet-programming-basics"></a>Základy internetového programování v prostředí MFC
Společnost Microsoft poskytuje mnoho rozhraní API pro programování klientské a serverové aplikace. Mnoho nových aplikací se zapisují pro Internet, a jako technologie, možnosti prohlížeče a změnit možnosti zabezpečení, budou zapisovat nových typů aplikací. Spuštění prohlížeče na klientských počítačích, které umožňují přístup k Internetu a zobrazení stránky HTML, které obsahují text, grafiky, ovládací prvky ActiveX a dokumenty. Servery poskytují FTP, HTTP a gopher služby a spuštění aplikací rozšíření server použití rozhraní CGI. Vlastní aplikace můžete načíst informace a poskytování dat na Internetu.  
  
 ![Klientské a serverové aplikace](../mfc/media/vc38bq1.gif "vc38bq1")  
  
 Knihovna MFC poskytuje třídy, které podporují internetové programování. Můžete použít [COleControl](../mfc/reference/colecontrol-class.md) a [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) a související třídy MFC k zápisu – ovládací prvky ActiveX a aktivní dokumenty. MFC – třídy můžete použít jako [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md), a [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) načíst soubory a informace, pomocí Internetové protokoly, jako HTTP a gopher.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Třídy MFC související s Internetem](../mfc/internet-related-mfc-classes.md)  
  
-   [Internetové informace podle témat](../mfc/internet-information-by-topic.md)  
  
-   [Internetové informace podle úloh](../mfc/internet-information-by-task.md)  
  
-   [Technologie Active na Internetu](../mfc/active-technology-on-the-internet.md)  
  
-   [WinInet – základy](../mfc/wininet-basics.md)  
  
-   [HTML – základy](../mfc/html-basics.md)  
  
-   [HTTP – základy](../mfc/http-basics.md)  
  
## <a name="related-sections"></a>Související oddíly  
  
-   [ActiveX – ovládací prvky na Internetu](../mfc/activex-controls-on-the-internet.md)  
  
-   [Aktivní dokumenty na Internetu](../mfc/active-documents-on-the-internet.md)  
  
-   [Asynchronní Monikery na Internetu](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)  
  
-   [Volby při návrhu aplikací](../mfc/application-design-choices.md)  
  
-   [Psaní aplikací MFC](../mfc/writing-mfc-applications.md)  
  
-   [Testování internetových aplikací](../mfc/testing-internet-applications.md)  
  
-   [Zabezpečení Internetu](../mfc/internet-security-cpp.md)  
  
-   [ATL – podpora pro ovládací prvky jazyka DHTML](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a>Weby pro další informace  
 Další informace o technologii Microsoft Internet najdete v tématu [Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/linkid=56322) webu. (Odkazy mohou bez předchozího oznámení změnit.)  
  
 Tento web pro vývojáře, obsahuje informace o používání vývojové nástroje společnosti Microsoft a technologie a nejdůležitější zprávy o poslední a nadcházející konferencí. Z této stránky můžete přejít na mnoho související vývojáře webů, včetně .NET a centra pro vývojáře XML. Můžete také stáhnout sady SDK beta a ukázky.  
  
 [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/linkid=37125) publikuje specifikace jazyka HTML, HTTP, CGI a další technologie webu.  
  
##  <a name="_core_more_internet_help"></a>Další nápovědu k Internetu  
 OLE část sady Windows SDK obsahuje další informace o programování OLE. Tyto informace obsahuje podrobné informace o používání funkce Win32 WinInet přímo, nikoli prostřednictvím třídy MFC. Obsahuje také základní informace o technologiích Internetu.  
  
## <a name="see-also"></a>Viz také  



