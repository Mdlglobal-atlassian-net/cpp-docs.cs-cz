---
title: Základy internetového programování v prostředí MFC
ms.date: 11/19/2018
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
ms.openlocfilehash: 5a8fb7bf07ec631869075c5977dcec468143ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366291"
---
# <a name="mfc-internet-programming-basics"></a>Základy internetového programování v prostředí MFC

Společnost Microsoft poskytuje mnoho rozhraní API pro programování klientských i serverových aplikací. Mnoho nových aplikací jsou psány pro Internet, a jako technologie, možnosti prohlížeče a možnosti zabezpečení změnit, nové typy aplikací budou zapsány. Prohlížeče běží v klientských počítačích, poskytují přístup k webu a zobrazují stránky HTML, které obsahují text, grafiku, ovládací prvky ActiveX a dokumenty. Servery poskytují služby FTP, HTTP a gopher a spouštějí aplikace pro rozšíření serveru pomocí rozhraní CGI. Vlastní aplikace může načítat informace a poskytovat data na Internetu.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace naleznete [v tématu ActiveX Controls](activex-controls.md).

![Klientské a serverové aplikace](../mfc/media/vc38bq1.gif "Klientské a serverové aplikace")

Knihovna MFC poskytuje třídy, které podporují programování v Internetu. [COleControl](../mfc/reference/colecontrol-class.md) a [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) a související třídy knihovny MFC můžete použít k zápisu ovládacích prvků ActiveX a aktivních dokumentů. Třídy knihovny MFC, například [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md)a [CAsyncMonikerFile,](../mfc/reference/casyncmonikerfile-class.md) můžete použít k načtení souborů a informací pomocí internetových protokolů, jako jsou FTP, HTTP a gopher.

## <a name="in-this-section"></a>V tomto oddílu

- [Třídy MFC související s internetem](../mfc/internet-related-mfc-classes.md)

- [Internetové informace podle témat](../mfc/internet-information-by-topic.md)

- [Internetové informace podle úloh](../mfc/internet-information-by-task.md)

- [Technologie Active na Internetu](../mfc/active-technology-on-the-internet.md)

- [WinInet – základy](../mfc/wininet-basics.md)

- [HTML – základy](../mfc/html-basics.md)

## <a name="related-sections"></a>Související oddíly

- [Ovládací prvky ActiveXna Internetu](../mfc/activex-controls-on-the-internet.md)

- [Asynchronní monikery na Internetu](../mfc/asynchronous-monikers-on-the-internet.md)

- [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)

- [Volby při návrhu aplikací](../mfc/application-design-choices.md)

- [Psaní aplikací MFC](../mfc/writing-mfc-applications.md)

- [Testování internetových aplikací](../mfc/testing-internet-applications.md)

- [Zabezpečení Internetu](../mfc/internet-security-cpp.md)

- [ATL – podpora pro ovládací prvky DHTML](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Další informace naleznete na webech

Další informace o internetových technologiích společnosti Microsoft naleznete na webu [microsoft developer network (MSDN).](https://go.microsoft.com/fwlink/p/?linkid=56322) (Odkazy se mohou změnit bez předchozího upozornění.)

Tento web pro vývojáře obsahuje informace o používání vývojových nástrojů a technologií společnosti Microsoft a hlavní informace o nedávných a nadcházejících konferencích. Na této stránce můžete přejít na mnoho souvisejících webů pro vývojáře, včetně center pro vývojáře .NET a XML. Můžete si také stáhnout beta sady SDK a ukázky.

[Konsorcium W3C (World Wide Web Consortium)](https://go.microsoft.com/fwlink/p/?linkid=37125) publikuje specifikace pro technologie HTML, HTTP, CGI a další chod webu.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Další nápověda k Internetu

Část OLE sady Windows SDK obsahuje další informace o programování OLE. Tyto informace poskytují podrobnosti o použití wininet wininet funkce přímo, nikoli prostřednictvím třídknihovny MFC. Obsahuje také přehled informací o internetových technologiích.
