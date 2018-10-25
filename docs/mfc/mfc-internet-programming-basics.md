---
title: Základy internetového programování MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2be02e6cac5dac226f7b04cd627a292e3761980
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082670"
---
# <a name="mfc-internet-programming-basics"></a>Základy internetového programování v prostředí MFC

Společnost Microsoft poskytuje řadu rozhraní API pro programování klientských i serverových aplikací. Jsou zapisovaná mnoho nových aplikací pro Internet, a technologií, možnosti prohlížeče a změnit možnosti zabezpečení, se zapíšou nových typů aplikací. Prohlížeče spustit na klientských počítačích, zajištění přístupu k webu a zobrazování stránky HTML, které obsahují text, grafiku, ovládací prvky ActiveX a dokumenty. Servery FTP, HTTP a gopher služby a spuštění serverové aplikace rozšíření rozhraní CGI. Vlastní aplikace můžete načíst informace a poskytují data na Internetu.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace najdete v tématu [ovládací prvky ActiveX](activex-controls.md).

![Klientské a serverové aplikace](../mfc/media/vc38bq1.gif "vc38bq1")

Knihovna MFC poskytuje třídy, které podporují programování na Internetu. Můžete použít [COleControl](../mfc/reference/colecontrol-class.md) a [cdocobjectserver –](../mfc/reference/cdocobjectserver-class.md) a související třídy knihovny MFC k tvorbě ovládacích prvků ActiveX a aktivní dokumenty. MFC – třídy můžete použít například [cinternetsession –](../mfc/reference/cinternetsession-class.md), [cftpconnection –](../mfc/reference/cftpconnection-class.md), a [casyncmonikerfile –](../mfc/reference/casyncmonikerfile-class.md) načíst soubory a informace, pomocí protokolů sítě Internet, jako je například FTP, HTTP a gopher.

## <a name="in-this-section"></a>V tomto oddílu

- [Třídy MFC související s internetem](../mfc/internet-related-mfc-classes.md)

- [Internetové informace podle témat](../mfc/internet-information-by-topic.md)

- [Internetové informace podle úloh](../mfc/internet-information-by-task.md)

- [Technologie Active na internetu](../mfc/active-technology-on-the-internet.md)

- [WinInet – základy](../mfc/wininet-basics.md)

- [HTML – základy](../mfc/html-basics.md)

## <a name="related-sections"></a>Související oddíly

- [Ovládací prvky ActiveX na internetu](../mfc/activex-controls-on-the-internet.md)

- [Asynchronní monikery na internetu](../mfc/asynchronous-monikers-on-the-internet.md)

- [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)

- [Volby při návrhu aplikací](../mfc/application-design-choices.md)

- [Psaní aplikací MFC](../mfc/writing-mfc-applications.md)

- [Testování internetových aplikací](../mfc/testing-internet-applications.md)

- [Internetové zabezpečení](../mfc/internet-security-cpp.md)

- [ATL – podpora ovládacích prvků DHTML](../atl/atl-support-for-dhtml-controls.md)

##  <a name="_core_web_sites_for_more_information"></a> Weby pro další informace

Další informace o technologii Microsoft Internet, najdete v článku [Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322) webu. (Odkazy mohou změnit bez předchozího upozornění.)

Tento web pro vývojáře obsahuje informace o použití Microsoft vývojářské nástroje a technologie a hlavní zprávy o poslední a nadcházející konference. Na této stránce můžete přejít na mnoho související vývojářské weby, včetně .NET a centra pro vývojáře XML. Můžete také stáhnout beta verze sady SDK a ukázky.

[World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125) publikuje specifikace HTML, protokolu HTTP, CGI a jiné webové technologie.

##  <a name="_core_more_internet_help"></a> Další nápovědu Internet

OLE – část sady Windows SDK obsahuje další informace o programování technologie OLE. Tyto informace obsahuje podrobnosti o použití funkce rozhraní Win32 WinInet přímo, namísto prostřednictvím třídy knihovny MFC. Také obsahuje souhrnné informace o technologiích Internet.

## <a name="see-also"></a>Viz také

