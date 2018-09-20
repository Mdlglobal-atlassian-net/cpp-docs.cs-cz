---
title: Slučování nabídek nápovědy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 379e67d00969518400826e1f82d8801391512ef4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435620"
---
# <a name="help-menu-merging"></a>Slučování nabídek nápovědy

Při objektu je aktivní v rámci kontejneru, v nabídce sloučení protokol dokumenty OLE poskytuje objekt úplnou kontrolu nad **pomáhají** nabídky. Témata nápovědy kontejneru v důsledku toho nejsou k dispozici, pokud uživatel deaktivuje objektu. Architektura zahrnutí aktivního dokumentu rozšíří na pravidlech pro místní nabídky sloučení umožňující kontejneru a aktivní dokument, který je aktivní sdílené složky v nabídce. Nová pravidla jsou jednoduše další konvence, o jakou součást vlastní jaké části nabídky a jak je vytvořený sdílené nabídky.

Nová konvence je jednoduché. V aktivní dokumenty **pomáhají** nabídka má dvě položky nabídek nejvyšší úrovně, které jsou průchody uspořádány takto:

`Help`

`Container Help >`

`Object Help    >`

Například část aplikace Word po aktivní v modul vazby sady Office, pak bude **pomáhají** nabídky bude vypadat následovně:

`Help`

`Binder Help >`

`Word Help   >`

Obě položky nabídky jsou podnabídky, za kterých žádné další položky nabídky konkrétní ke kontejneru a objektu jsou k dispozici pro uživatele. Které položky se zobrazí zde bude lišit podle kontejnerů a objektů zahrnuté.

K vytvoření to sloučit **pomáhají** nabídky, architektura zahrnutí aktivního dokumentu upraví běžný postup dokumenty OLE. Podle dokumenty OLE, sloučené nabídek můžete mít šest skupiny nabídek, konkrétně **souboru**, **upravit**, **kontejneru**, **objekt**,  **Okno**, **pomáhají**v tomto pořadí. V každé skupině může být nula nebo více nabídek. Skupiny **souboru**, **kontejneru**, a **okno** patřit do kontejneru a skupiny **upravit**, **objektu,** a **pomáhají** patřit do objektu. Pokud objekt chce udělat, slučování nabídek, vytvoří prázdné nabídek a předává je do kontejneru. Kontejneru poté vloží do jeho nabídky, zavoláním `IOleInPlaceFrame::InsertMenus`. Objekt také předává strukturu, která je pole šest dlouhé hodnoty (**OLEMENUGROUPWIDTHS**). Po vložení nabídky, označí kontejneru přidá v každém z nich svých skupin a potom vrátí počet nabídek. Objekt vloží nabídky, dejte pozor na počet nabídek, které se v každé skupině kontejnerů. Nakonec se objekt předá sloučené nabídek a pole (který obsahuje počet nabídek, které v jednotlivých skupinách) OLE, která vrátí neprůhledný "popisovač nabídky" zpracování. Později objekt předá tento popisovač a řádku nabídek sloučené do kontejneru, prostřednictvím `IOleInPlaceFrame::SetMenu`. V současné době kontejner zobrazí sloučené nabídek a také předá popisovač OLE, tak, aby OLE můžete provést řádné odesílání zpráv nabídky.

V postupu upravené aktivní dokument, musí nejprve inicializovat objekt **OLEMENUGROUPWIDTHS** prvky hodnotě nula. před předáním do kontejneru. Potom kontejner provádí vkládání normální nabídky s jednou výjimkou: Vloží kontejneru **pomáhají** jako poslední položky nabídky a uloží hodnotu 1 v poslední položky (šestého) **OLEMENUGROUPWIDTHS** pole (to znamená, šířka [5], který patří do skupiny nápovědy objektu). To **pomáhají** nabídky budou mít pouze jednu položku, která je podnabídky, "**nápovědy kontejneru** >" cascade nabídky, jak je uvedeno výše.

Objekt pak spustí jeho kód vložení normální nabídky, s výjimkou, že před vložením jeho **pomáhají** nabídky, zkontroluje šestého záznam **OLEMENUGROUPWIDTHS** pole. Pokud hodnota je 1 a název nabídky poslední **pomáhají** (nebo odpovídající lokalizovaný řetězec), pak vloží objekt jeho **pomáhají** menu jako podnabídky kontejneru **pomáhají** nabídka.

Potom nastaví šestého prvku v objektu **OLEMENUGROUPWIDTHS** na nulu a pátého prvku pole se zvýší o hodnotu jedna. Díky tomu OLE vědět, že **pomáhají** nabídky patří do tohoto kontejneru a zprávy nabídky odpovídající této nabídky (a její podnabídky) se mají směrovat do tohoto kontejneru. Zodpovídá za pak kontejneru předávat **WM_INITMENUPOPUP**, **WM_SELECT**, **wm_command –** a další zprávy týkající se nabídky, které patří do objektu část **pomáhají** nabídky. To lze provést pomocí **WM_INITMENU** Vymazat příznak, který určuje kontejner, jestli má uživatel přešel do objektu **pomáhají** nabídky. Kontejner pak sleduje **WM_MENUSELECT** vstupu nebo výstupu z libovolné položky na **pomáhají** nabídky, která kontejner sám nebyl přidán. V položce, znamená to uživatel přešel do nabídky objektu tak, aby kontejneru nastaví příznak "v nabídce Nápověda pro objekt" a používá stav tohoto příznaku předávat žádné **WM_MENUSELECT**, **WM_INITMENUPOPUP**a  **Wm_command –** zprávy, minimálně, do okna objekt. (Při ukončení kontejneru příznak a poté zpracuje tyto stejné zprávy samotný.) Kontejneru měli použít okno vrácená z objektu `IOleInPlaceActiveObejct::GetWindow` fungovat jako cíl pro tyto zprávy.

Pokud objekt zjistí nulu v šestého prvku v **OLEMENUGROUPWIDTHS**, pokračuje podle běžných pravidel pro dokumenty OLE. Tento postup popisuje kontejnery, které jsou součástí **pomáhají** i těch, které nejsou slučováním nabídek.

Při volání objektu `IOleInPlaceFrame::SetMenu`, než zobrazení sloučené nabídek, kontejner kontroly, jestli **pomáhají** nabídka obsahuje další podnabídky, kromě co byl vložen kontejneru. Pokud tedy kontejneru opustí jeho **pomáhají** nabídky v pruhu sloučené nabídky. Pokud **pomáhají** nabídky nemá žádné další podnabídky, kontejneru se odeberou jeho **pomáhají** nabídku z řádku nabídek sloučené. Tento postup popisuje objekty, které jsou součástí **pomáhají** i těch, které nejsou slučováním nabídek.

A konečně, když je čas na převod ze strojového kódu v nabídce, objekt odebere vloženého **pomáhají** nabídky kromě odebrat další vložen nabídky. Když kontejneru odebere jeho nabídky, odebere jeho **pomáhají** nabídky kromě jiných nabídek, které se má vložit.

## <a name="see-also"></a>Viz také

[Kontejnery pro aktivní dokument](../mfc/active-document-containers.md)

