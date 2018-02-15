---
title: Automatizace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0204ab105b48350ea7fe934c28c5d5f95bea71f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="automation"></a>Automatizace
Automatizace (dříve označované jako automatizace OLE) umožňuje jednu aplikaci k manipulaci s objekty, které jsou implementovány v jiné aplikaci, nebo ke zveřejnění objekty, budou se dá upravit.  
  
 [Automatizační server](../mfc/automation-servers.md) je aplikace (typ COM server), která zveřejňuje jeho funkce prostřednictvím rozhraní modelu COM k ostatním aplikacím volat [klienti automatizace](../mfc/automation-clients.md). Expozici umožňuje klientům automatizace automatizovat určité funkce přímo přístup k objektům a použitím služby, které poskytují.  
  
 Automatizační servery a klienty použijte rozhraní modelu COM, které jsou vždy odvozeny od `IDispatch` a přijmout a vrátit konkrétní sadu datových typů s názvem typy Automation. Je možné automatizovat libovolný objekt, který zveřejňuje automatizace rozhraní, poskytuje metody a vlastnosti, kterým můžete přistupovat z jiných aplikací. Automatizace je k dispozici pro objekty OLE a COM. Automatizované objekt může být místní nebo vzdálené (na jiném počítači přístupné přes síť); proto existují dvě kategorie automatizace:  
  
-   Automatizovaná (místní počítač).  
  
-   Vzdálená automatizace (přes síť pomocí Distributed COM nebo DCOM).  
  
 Vystavení objektů je užitečné, když aplikace poskytují funkce, které jsou užitečné k ostatním aplikacím. Například ovládacího prvku ActiveX je typ automatizační server; hostování ovládacího prvku ActiveX aplikace je klient automatizace tohoto ovládacího prvku.  
  
 Další příklad textový editor mohou být vystaveny jeho pravopisu funkce do jiných programů. Vystavení objektů, které umožňuje dodavatelům ke zlepšení svých aplikacích pomocí připravených funkce jiných aplikací. Tímto způsobem se vztahuje automatizace některé ze zásad objektově orientované programování, jako je například – opětovné použití a zapouzdření na úrovni aplikace, sami.  
  
 Důležitější se na technickou podporu, které Automation nabízí uživatelům a poskytovatelé řešení. Díky zpřístupnění funkcí aplikace pomocí běžných, dobře definované rozhraní, Automation umožňuje vytvořit komplexní řešení v jednom Obecné programovací jazyk, jako je například Microsoft Visual Basic, místo v různých Makro specifické pro aplikaci jazyky.  
  
 Mnoho obchodních aplikací, jako je například aplikace Microsoft Excel a Microsoft Visual C++, umožňují automatizovat většinu jejich funkce. Například v jazyce Visual C++, může zapisovat makra jazyk VBScript k automatizaci sestavení, aspektů kód úprav a ladění úloh.  
  
##  <a name="_core_passing_parameters_in_automation"></a> Předávání parametrů v automatizace  
 Jeden potíže při vytváření automatizace metody pomáhá zajistit uniform "bezpečnou" mechanismus k předávání dat mezi automatizační servery a klienty. Automatizace používá **VARIANT** typ k předávání dat. **VARIANT** je typ s příznakem union. Obsahuje člena dat pro hodnotu (jedná se anonymní sjednocení C++) a data člena označující typ informací uložených v sjednocení. **VARIANT** typu podporuje několik standardní datových typů: 2 a 4 bajtů celá čísla, čísla s plovoucí desetinnou čárkou 4 a 8 bajtů, řetězce a logické hodnoty. Kromě toho podporuje `HRESULT` (OLE kódy chyb), **MĚNA** (s pevnou desetinnou čárkou číselný typ.), a **datum** (absolutní datum a čas), typy a také odkazy na **IUnknown**  a `IDispatch` rozhraní.  
  
 **VARIANT** typ je zapouzdřené v [COleVariant](../mfc/reference/colevariant-class.md) třídy. V podporu **MĚNA** a **datum** třídy jsou zapouzdřené v [COleCurrency](../mfc/reference/colecurrency-class.md) a [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) třídy.  
  
## <a name="automation-samples"></a>Ukázky automatizace  
  
-   [AUTOCLIK](../visual-cpp-samples.md) tuto ukázku použít další techniky automatizace a jako základ pro učení vzdálené automatizace.  
  
-   [Acdual –](../visual-cpp-samples.md) přidá duální rozhraní k aplikaci serveru automatizace.  
  
-   [CALCDRIV](../visual-cpp-samples.md) řídí MFCCALC automatizace klientské aplikace.  
  
-   [INPROC](../visual-cpp-samples.md) ukazuje aplikace server automatizace v procesu.  
  
-   [IPDRIVE](../visual-cpp-samples.md) řídí INPROC automatizace klientské aplikace.  
  
-   [MFCCALC](../visual-cpp-samples.md) ukazuje automatizace klientské aplikace.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Klienti automatizace](../mfc/automation-clients.md)  
  
-   [Automatizační servery](../mfc/automation-servers.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [Technologie Active](../mfc/mfc-com.md)  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat  
  
-   [Přidejte třídu automatizace](../mfc/automation-servers.md)  
  
-   [Použití knihovny typů](../mfc/automation-clients-using-type-libraries.md)  
   
-   [Automatizační servery přístupu](../mfc/automation-servers.md)  
  
-   [Klienti automatizace zápis v jazyce C++](../mfc/automation-clients.md)  
  
## <a name="see-also"></a>Viz také  
 [MFC COM](../mfc/mfc-com.md)
