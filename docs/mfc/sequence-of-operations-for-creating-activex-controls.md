---
title: Posloupnost operací při vytváření ovládacích prvků ActiveX
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
ms.openlocfilehash: d9025c2a4192b5a2c08d1af9dc925378cff9f504
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632788"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>Posloupnost operací při vytváření ovládacích prvků ActiveX

V následující tabulce jsou uvedeny vaši roli a roli v rámci při vytváření ovládacích prvků ActiveX (dříve označované jako ovládací prvky OLE).

### <a name="creating-activex-controls"></a>Vytváření ovládacích prvků ActiveX

|Úloha|Můžete provést|Nepodporuje rozhraní framework|
|----------|------------|------------------------|
|Vytvoření rozšiřovatelnou platformu pro ovládací prvek ActiveX.|Spusťte průvodce ovládací prvek ActiveX knihovny MFC k vytvoření ovládacího prvku. Zadejte požadované možnosti na stránkách možností. Mezi možnosti patří typ a název ovládacího prvku v projektu, licencování, vytváření podtříd a metodu o pole.|Průvodce pro ovládací prvek ActiveX knihovny MFC vytvoří soubory pro ovládací prvek ActiveX se základní funkčností, včetně zdrojových souborů pro aplikace, ovládací prvek a stránku vlastností nebo stránky. soubor prostředků; soubor projektu; a jiné, všechny přizpůsobené vašich požadavků.|
|Zjistěte, co ovládací prvek a Průvodce ovládacím prvkem ActiveX bez přidání psát vlastní kód.|Vytváření ovládacího prvku ActiveX a testování s aplikací Internet Explorer nebo [lze kontejner TSTCON ukázka](../visual-cpp-samples.md).|Spuštěné ovládací prvek má schopnost velikost a umístění. Je také **pole o** – metoda (Pokud je vybrána), který lze vyvolat.|
|Implementace metod a vlastností ovládacího prvku.|Implementace metody specifické pro ovládací prvek a vlastnosti přidáním členské funkce a poskytuje vystavené rozhraní pro data ovládacího prvku. Přidání členské proměnné, která bude uchovávat datových struktur a použití obslužných rutin událostí k vyvolání události při zjišťování.|Rozhraní již definována mapu, která podporují události, vlastnosti a metody, které byste museli opustit vám umožní zaměřit se na tom, jak jsou implementované vlastnosti a metody ovládacího prvku. Výchozí stránky vlastností je možné zobrazit a není zadána výchozí metoda o pole.|
|Vytvoření ovládacího prvku stránku nebo stránky vlastností.|Pomocí editory prostředků Visual C++ lze upravit vizuálně rozhraní stránky vlastností ovládacího prvku:<br /><br />-Vytvořte další stránky vlastností.<br />– Vytvoření a úprava rastrové obrázky, ikony a kurzory.<br /><br /> V editoru dialogového okna můžete také testovat stránky vlastností.|Výchozí soubor prostředků vytvořený pomocí Průvodce aplikací knihovny MFC poskytuje mnoho prostředků, které potřebujete. Visual C++ umožňuje upravovat existující prostředky a snadno a vizuálně přidat nové prostředky.|
|Otestujte události, metody a vlastnosti ovládacího prvku.|Znovu sestavte ovládací prvek a použít kontejner testu k otestování vaší obslužné rutiny fungovat správně.|Můžete volat metody ovládacího prvku a manipulaci s jeho vlastnosti prostřednictvím rozhraní stránky vlastností nebo pomocí testovacího kontejneru. Kromě toho pomocí testovacího kontejneru sledování událostí vyvolaných z ovládacího prvku a oznámení přijímaná kontejneru ovládacího prvku.|

## <a name="see-also"></a>Viz také

[Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)<br/>
[Posloupnost operací při sestavování aplikací MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Posloupnost operací při vytváření aplikací OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Posloupnost operací při vytváření databázových aplikací](../mfc/sequence-of-operations-for-creating-database-applications.md)

