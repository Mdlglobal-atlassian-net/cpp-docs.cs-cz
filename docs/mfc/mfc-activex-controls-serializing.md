---
title: "Ovládací prvky MFC ActiveX: Serializace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34b8f0520d1f071bb408f782b0f2370ef29f528e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-serializing"></a>MFC – ovládací prvky ActiveX: Serializace
Tento článek popisuje, jak k serializaci ovládacího prvku ActiveX. Serializace je proces čtení nebo zápisu do trvalého úložiště média, jako je soubor na disku. Knihovna Microsoft Foundation Class (MFC) obsahuje integrovanou podporu pro serializaci ve třídě `CObject`. `COleControl`rozšiřuje tato podpora do ovládacích prvků ActiveX prostřednictvím mechanismus vlastnost exchange.  
  
 Serializace pro ovládací prvky ActiveX je implementováno modulem přepsání [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Tato funkce volána v průběhu načítání a ukládání objektu ovládacího prvku, uloží všechny vlastnosti implementovaný pomocí členské proměnné nebo členské proměnné s upozornění na změnu.  
  
 V následujících tématech najdete hlavní problémy související s serializaci ovládacího prvku ActiveX:  
  
-   Implementace `DoPropExchange` funkce určená k serializaci objektu ovládacího prvku  
  
-   [Přizpůsobení procesu serializace](#_core_customizing_the_default_behavior_of_dopropexchange)  
  
-   [Implementace podpora verzí](#_core_implementing_version_support)  
  
##  <a name="_core_implementing_the_dopropexchange_function"></a>Implementace dopropexchange – funkce  
 Pokud použijete Průvodce ovládacím prvkem ActiveX ke generování řízení projektu, několik Výchozí obslužná rutina automaticky přidány do třídy ovládacího prvku, včetně výchozí implementaci [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Následující příklad ukazuje kód přidat do třídy, které jsou vytvořené pomocí Průvodce ovládacím prvkem ActiveX:  
  
 [!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]  
  
 Pokud chcete, aby vlastnost trvalé, upravte `DoPropExchange` tak, že přidáte volání funkce exchange vlastnost. Následující příklad ukazuje serializace vlastní vlastnost Boolean CircleShape, kde vlastnost CircleShape má výchozí hodnotu **TRUE**:  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]  
  
 Následující tabulka uvádí funkce exchange možné vlastností, které můžete použít k serializaci vlastností ovládacího prvku:  
  
|Funkce výměny vlastnost|Účel|  
|---------------------------------|-------------|  
|**Px_blob –)**|Serializuje typu vlastnosti dat binární velkého objektu (binární rozsáhlý OBJEKT).|  
|**Px_bool –)**|Serializuje typu vlastnost typu Boolean.|  
|**Px_color –)**|Serializuje barva vlastnost typu.|  
|**Px_currency –)**|Serializuje typu **CY** vlastnost (měna).|  
|**Px_double –)**|Serializuje typu **dvojité** vlastnost.|  
|**Px_font –)**|Serializuje vlastnost typ písma.|  
|**Px_float –)**|Serializuje typu **float** vlastnost.|  
|**Px_iunknown –)**|Serializuje vlastnost typu `LPUNKNOWN`.|  
|**Px_long –)**|Serializuje typu **dlouho** vlastnost.|  
|**Px_picture –)**|Serializuje typu vlastnosti obrázek.|  
|**Px_short –)**|Serializuje typu **krátké** vlastnost.|  
|**(PXstring)**|Serializuje typu `CString` vlastnost.|  
|**Px_ulong –)**|Serializuje typu **ULONG** vlastnost.|  
|**Px_ushort –)**|Serializuje typu **USHORT** vlastnost.|  
  
 Další informace o těchto funkcích vlastnost exchange najdete v tématu [trvalost z ovládacích prvků technologie OLE](../mfc/reference/persistence-of-ole-controls.md) v *odkaz knihovny MFC*.  
  
##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Přizpůsobení výchozího chování dopropexchange –  
 Výchozí implementaci **DoPropertyExchange** (jak je znázorněno v předchozích tématu) zavolá základní třída `COleControl`. To serializuje sada vlastností, které automaticky nepodporuje `COleControl`, který používá další úložný prostor než serializaci vlastní vlastnosti ovládacího prvku. Odebrání toto volání umožňuje objektu k serializaci pouze vlastnosti, které považujete za důležité. Všechny stavy uložených vlastností ovládacího prvku implementovala nebude serializovat, když uložení nebo načtení objekt ovládacího prvku, pokud je explicitně přidat **PX_** volání pro ně.  
  
##  <a name="_core_implementing_version_support"></a>Implementace podpora verzí  
 Podpora verzí umožňuje revidovaný ovládacího prvku ActiveX k přidání nových vlastností trvalé a přitom zachovat ke zjišťování a načíst trvalý stav vytvořena ve starší verzi ovládacího prvku. Chcete-li zpřístupnit verzi ovládacího prvku v rámci trvalé data, volání [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) v ovládacím prvku `DoPropExchange` funkce. Toto volání se automaticky vložený, pokud ovládací prvek ActiveX byla vytvořena pomocí Průvodce ovládacím prvkem ActiveX. Může být odebrán, pokud není nutné podpora verzí. Náklady na ovládací prvek velikost je však velmi malé (4 bajtů) pro flexibilnější, která poskytuje podporu verzí.  
  
 Pokud ovládací prvek nebyl vytvořen pomocí Průvodce ovládacím prvkem ActiveX, že přidáte volání `COleControl::ExchangeVersion` vložením následující řádek na začátku vaše `DoPropExchange` – funkce (před voláním `COleControl::DoPropExchange`):  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 Můžete použít libovolnou `DWORD` jako číslo verze. Použijte projekty generované Průvodce ovládacím prvkem ActiveX **_wVerMinor** a **_wVerMajor** jako výchozí. Jsou to globální konstanty definované v souboru implementace třídy ovládacího prvku ActiveX projektu. V rámci zbytek vaší `DoPropExchange` funkce, můžete volat [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) kdykoli načíst verzi jsou uložení nebo načítání.  
  
 V následujícím příkladu má verze 1 Tento ovládací prvek ukázka pouze vlastnost "ReleaseDate". Verze 2 přidá vlastnost "OriginalDate". Pokud se načíst trvalý stav z předchozí verzi aplikace je odeslán pokyn ovládacího prvku, inicializuje členské proměnné nové vlastnosti na výchozí hodnotu.  
  
 [!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 Ve výchozím nastavení ovládacího prvku "převede" stará data na nejnovější formát. Například pokud verze 2 ovládacího prvku načítá data, která byla uložena podle verze 1, se bude zapisovat ve formátu verze 2 při jeho uložení opakujte. Pokud chcete k uložení dat v poslední čtení formátu ovládacího prvku, předat **FALSE** jako třetí parametr při volání metody `ExchangeVersion`. Tato třetí parametr je volitelný a je **TRUE** ve výchozím nastavení.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

