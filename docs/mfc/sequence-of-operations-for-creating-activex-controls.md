---
title: Posloupnost operací při vytváření ovládacích prvků ActiveX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: caf4c74f2263505ad5d7112021003f92c85a4b84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380367"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>Posloupnost operací při vytváření ovládacích prvků ActiveX
V následující tabulce jsou vaše role a role rozhraní framework v vytváření ovládacích prvků ActiveX (dříve označované jako ovládací prvky OLE).  
  
### <a name="creating-activex-controls"></a>Vytváření ovládacích prvků ActiveX  
  
|Úloha|Můžete provést|Nepodporuje rozhraní|  
|----------|------------|------------------------|  
|Vytvořte představuje rozhraní pro ovládací prvek ActiveX.|Spusťte Průvodce ovládacím prvkem ActiveX knihovny MFC k vytvoření vlastního ovládacího prvku. Zadejte požadované možnosti na stránkách možnosti. Možnosti zahrnují typ a název ovládacího prvku v projektu, licencí, vytváření podtříd a metodu o pole.|Průvodce ovládacím prvkem ActiveX knihovny MFC vytvoří soubory pro ovládací prvek ActiveX s základní funkce, včetně zdrojových souborů pro aplikace, ovládací prvek a vlastnost stránku nebo stránky; soubor prostředků; soubor projektu; a jiné, všech podle vašich požadavků.|  
|Zjistěte, co ovládací prvek a Průvodce ovládacím prvkem ActiveX bez přidání řádek vlastní kód.|Vytvoření ovládacího prvku ActiveX a otestovat ji s aplikací Internet Explorer nebo [TSTCON ukázka](../visual-cpp-samples.md).|Spuštěné řízení má možnost ke změně velikosti a přesunout. Je také **o pole** metoda (Pokud je vybraná), která se může vyvolat.|  
|Implementace metod a vlastností ovládacího prvku.|Implementujte řízení konkrétní metody a vlastnosti přidáním členské funkce zajistit zveřejněné rozhraní data ovládacího prvku. Přidání členské proměnné pro uložení datové struktury vyvolání události při zjistíte pomocí obslužných rutin událostí.|Rozhraní framework již definována mapu, která bude podporovat události, vlastnosti a metody, a zaměřit na tom, jak jsou implementované vlastnosti a metody ovládacího prvku. Stránka vlastností výchozí jsou viditelná a poskytuje metodu o pole výchozí.|  
|Vytvoření ovládacího prvku stránku nebo stránky vlastností.|Pomůže vizuálně upravit rozhraní stránky vlastností ovládacího prvku editory prostředků Visual C++:<br /><br /> -Vytvořte další stránky vlastností.<br />-Vytvořit a upravit rastrové obrázky, ikony a kurzory.<br /><br /> V editoru dialogového okna můžete také otestovat stránky vlastností.|Výchozí soubor prostředků vytvořené průvodcem aplikací MFC poskytuje řadu zdrojů, které potřebujete. Visual C++ umožňuje upravit existující prostředky a přidat nové prostředky snadno a vizuálně.|  
|Otestujte události, metod a vlastností ovládacího prvku.|Opětovné sestavení ovládacího prvku a použít testovací kontejner pro testování vaší obslužné rutiny fungovat správně.|Můžete volat metody ovládacího prvku a upravit jeho vlastnosti prostřednictvím rozhraní vlastnost stránky nebo – kontejner testů. Kromě toho pomocí testovacího kontejneru sledovat události aktivována z ovládacího prvku a oznámení přijímaná kontejneru ovládacího prvku.|  
  
## <a name="see-also"></a>Viz také  
 [Vytváření v rozhraní Framework](../mfc/building-on-the-framework.md)   
 [Posloupnost operací při sestavování aplikací MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Posloupnost operací při vytváření aplikací OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Posloupnost operací při vytváření databázových aplikací](../mfc/sequence-of-operations-for-creating-database-applications.md)

