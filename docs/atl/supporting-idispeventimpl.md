---
title: Podpora IDispEventImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 680396ae912cca5f19e87697e7de0033213cc963
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362216"
---
# <a name="supporting-idispeventimpl"></a>Podpora IDispEventImpl
Šablony třídy [IDispEventImpl](../atl/reference/idispeventimpl-class.md) slouží k zajištění podpory pro připojení bodu jímky ve třídě ATL. Jímka bodu připojení umožňuje třídě zpracování událostí aktivována z externích objektů COM. Tyto jímky bodu připojení jsou mapovány s mapou podřízený události poskytované třídě.  
  
 Správně implementovat jímka bodu připojení pro třídu, musí dokončit následující kroky:  
  
-   Import knihovny typů pro každý externí objekt  
  
-   Deklarovat `IDispEventImpl` rozhraní  
  
-   Deklarace mapy jímek událostí  
  
-   Poradit a unadvise body připojení  
  
 Kroky implementace jímka bod připojení se provádí úpravou pouze soubor hlaviček () vaší třídy.  
  
## <a name="importing-the-type-libraries"></a>Import knihovny typů  
 Pro každý externí objekt jehož události chcete zpracovat je nutné naimportovat knihovny typů. Tento krok definuje události, které mohou být zpracovány a poskytuje informace, které se používá při deklarování mapy jímek událostí. [#Import](../preprocessor/hash-import-directive-cpp.md) – direktiva může k tomu použít. Přidat nezbytné `#import` direktivy řádků pro každé rozhraní odesílání bude podporovat k soubor hlaviček () vaší třídy.  
  
 Následující příklad importuje knihovny typů externího serveru COM (`MSCAL.Calendar.7`):  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  Musíte mít samostatný `#import` příkaz pro každý typ externího knihovny bude podporovat.  
  
## <a name="declaring-the-idispeventimpl-interfaces"></a>Deklarování rozhraní IDispEventImpl  
 Teď, když jste importovali knihoven typů každého rozhraní dispatch, je třeba deklarovat samostatné `IDispEventImpl` rozhraní pro jednotlivá rozhraní externí odesílání. Prohlášení o třídě upravit přidáním `IDispEventImpl` rozhraní deklarace pro každý externí objekt. Další informace o parametrech najdete v tématu [IDispEventImpl](../atl/reference/idispeventimpl-class.md).  
  
 Následující kód deklaruje pro dvě jímky bodu připojení, `DCalendarEvents` rozhraní pro objekt COM implementováno třídou `CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]  
  
## <a name="declaring-an-event-sink-map"></a>Deklarace mapy jímek událostí  
 V pořadí pro oznamování událostí ke zpracování pomocí správné funkce musí třídě směrovat všechny události její správné obslužné rutině. Toho se dosáhne deklarace mapy jímek událostí.  
  
 ATL poskytuje několik makra [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map), a [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), který snazší toto mapování. Standardní formát vypadá takto:  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `. . . //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 Následující příklad deklaruje mapou podřízený události s dvě obslužné rutiny událostí:  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]  
  
 Implementace je téměř dokončena. Poslední krok se týká informací a unadvising externí rozhraní.  
  
## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Poradenství a Unadvising IDispEventImpl rozhraní  
 Posledním krokem je implementace metodu, která bude poradit (nebo unadvise) všechny body připojení v době správné. Tato radí je třeba provést před může probíhat komunikace mezi externích klientů a objektu. Před objektu se zobrazí, je každé rozhraní externí odesílání nepodporuje objektu dotazován pro odchozí rozhraní. Vytvoření připojení a odkaz na rozhraní odchozí slouží ke zpracování událostí z objektu. Tento postup se označuje jako "radí."  
  
 Po dokončení objektu s externí rozhraní mají být upozorněni odchozí rozhraní, že se už používají ve třídě. Tento proces se označuje jako "unadvising."  
  
 Z důvodu jedinečné povaha objekty modelu COM tento postup se liší v podrobností a provádění mezi implementace. Tyto podrobnosti jsou nad rámec tohoto tématu, nejsou řešit.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)

