---
title: Uložené vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- stock properties, about stock properties
- stock properties
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 201e6f0591d446dc0e6b036cfd7ac6f3028eb812
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430259"
---
# <a name="stock-properties"></a>Uložené vlastnosti

Pokud přidáváte vlastnost dispinterface MFC pomocí [Průvodce přidáním vlastnosti](../ide/idl-attributes-add-property-wizard.md), můžete použít uložených vlastností z **název vlastnosti** v seznamu [názvy](../ide/names-add-property-wizard.md) stránku Průvodce. Tyto vlastnosti jsou následující:

|Název vlastnosti|Popis|
|-------------------|-----------------|
|**Vzhled**|Vrací nebo nastavuje hodnotu, která určuje vzhled ovládacího prvku. Ovládací prvek **vzhled** vlastnosti můžete zahrnout nebo vynechejte efekty trojrozměrného zobrazení. To je vlastnost okolí čtení a zápisu.|
|`BackColor`|Vrací nebo nastavuje okolí ovládacího prvku `BackColor` vlastnost barvu z palety (RGB) nebo předdefinovaných systémových barev. Ve výchozím nastavení jeho hodnota odpovídá barvu popředí ovládacího prvku kontejneru. To je vlastnost okolí čtení a zápisu.|
|`BorderStyle`|Vrátí nebo nastaví styl ohraničení ovládacího prvku. Toto je vlastnost pro čtení a zápisu.|
|**Titulek**|Vrátí nebo nastaví ovládací prvek **titulek** vlastnost. Popisek je záhlaví okna. **Titulek** nemá žádné **členskou proměnnou** typ implementace.|
|**Povoleno**|Vrátí nebo nastaví ovládací prvek **povoleno** vlastnost. Ovládací prvek povolený může reagovat na události generované uživatelem.|
|**Písma**|Vrátí nebo nastaví písmo ovládacího prvku. Hodnota Null, pokud ovládací prvek nemá žádné písmo.|
|`ForeColor`|Vrací nebo nastavuje okolí ovládacího prvku `ForeColor` vlastnost.|
|**hWnd**|Vrátí nebo nastaví ovládací prvek **hWnd** vlastnost. **hWnd** nemá žádné **členskou proměnnou** typ implementace.|
|**Objekt ReadyState**|Vrátí nebo nastaví ovládací prvek **ReadyState** vlastnost. Ovládací prvek může být neinicializované, inicializován, načítání, interaktivní nebo dokončení. Zobrazit [READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx) v *Internet SDK* Další informace.|
|**Text**|Vrátí nebo nastaví text obsažen v ovládacím prvku. **Text** nemá žádné **členskou proměnnou** typ implementace.|

## <a name="see-also"></a>Viz také

[Přidání vlastnosti](../ide/adding-a-property-visual-cpp.md)<br>
[IDL – atributy, Průvodce přidáním vlastnosti](../ide/idl-attributes-add-property-wizard.md)