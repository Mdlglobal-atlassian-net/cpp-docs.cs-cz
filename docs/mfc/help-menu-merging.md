---
title: "Slučování nabídek nápovědy | Microsoft Docs"
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
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c4d3ae9509edcbe79417bb37d02f4f585b2da653
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="help-menu-merging"></a>Slučování nabídek nápovědy
Když objekt je aktivní v rámci kontejneru, v nabídce slučování protokol OLE dokumentů umožňuje dokončení řízení objektu **pomoci** nabídky. Témata nápovědy kontejneru v důsledku toho nejsou k dispozici, pokud uživatel deaktivuje objektu. Architektura zahrnutí aktivního dokumentu rozšíří v pravidlech pro místní nabídky slučování umožňující active dokumentu, který je aktivní sdílet v nabídce a kontejneru. Nová pravidla jsou jednoduše další konvence, o jaké součásti vlastní jaké části nabídky a jak je vytvořený sdílené nabídky.  
  
 Nové konvence je jednoduché. V aktivní dokumenty **pomoci** nabídky má dvě položky nabídek nejvyšší úrovně uspořádána následujícím způsobem:  
  
 `Help`  
  
 `Container Help >`  
  
 `Object Help    >`  
  
 Například Word části po aktivní v vazby sady Office, pak se **pomoci** nabídky by měly vypadat následovně:  
  
 `Help`  
  
 `Binder Help >`  
  
 `Word Help   >`  
  
 Obě položky nabídky jsou kaskádové nabídky, pod kterým jsou uvedeny všechny položky další nabídky konkrétní ke kontejneru a objektu pro uživatele. Co položky objeví tady se bude lišit podle kontejneru a objekty související se situací.  
  
 K vytvoření to sloučit **pomoci** nabídce architektura zahrnutí aktivního dokumentu upraví běžný postup OLE dokumenty. Podle dokumenty OLE, panelu nabídek sloučené mít šest skupiny nabídek, konkrétně **soubor**, **upravit**, **kontejneru**, `Object`, **okno**, **Pomoci**, v tomto pořadí. V každé skupině může být nula nebo více nabídek. Skupiny **soubor**, **kontejneru**, a **okno** patřit do kontejneru a skupiny **upravit**, **objektu,** a **pomoci** patří k objektu. Pokud objekt chce provést slučování nabídek, vytvoří prázdné nabídek a předává je do kontejneru. Kontejner pak vloží do jeho nabídky voláním **IOleInPlaceFrame::InsertMenus**. Objekt také předá strukturu, která je pole šesti dlouhé hodnoty (**OLEMENUGROUPWIDTHS**). Po vložení v nabídkách, označí kontejneru kolik nabídky ho přidat v každé z nich jeho skupin a potom se vrátí. Objekt pak vloží jeho nabídky důrazem počet položek nabídky v každé skupině kontejneru. Nakonec se objekt předá sloučené nabídek a pole (který obsahuje počet položek nabídky v každé skupině) OLE, která vrátí neprůhledné "nabídky popisovač" zpracování. Později objekt předá tento popisovač a řádku nabídek sloučené do kontejneru, prostřednictvím **IOleInPlaceFrame::SetMenu**. V tomto okamžiku kontejner zobrazí panelu sloučené nabídek a také předá popisovač OLE, takže OLE využít správné odeslání zpráv nabídky.  
  
 V postupu změny aktivní dokument, musí nejprve inicializovat objekt **OLEMENUGROUPWIDTHS** elementy na nulu před jeho odesláním do kontejneru. Potom kontejner provede normální nabídky vkládání s jednou výjimkou: vložení kontejneru **pomoci** nabídky jako poslední položky a ukládá na hodnotu 1 v poslední položky (šesté) **OLEMENUGROUPWIDTHS** pole (to znamená, šířka [5], který patří do skupiny objektu Nápověda). To **pomoci** nabídky budou mít jen jednu položku, která je dílčí, "**kontejneru nápovědy** >" cascade nabídky výše popsané.  
  
 Objekt pak provede jeho normální nabídky vložení kódu, vyjma toho, že před vložením jeho **pomoci** nabídce zkontroluje šesté položku **OLEMENUGROUPWIDTHS** pole. Pokud hodnota je 1, název poslední nabídky **pomoci** (nebo odpovídající lokalizovaný řetězec), pak vloží objekt jeho **pomoci** nabídky jako dílčí kontejneru **pomoci** nabídky.  
  
 Objekt nastaví šesté elementu **OLEMENUGROUPWIDTHS** na hodnotu nula a zvýší páté elementu jednou. To umožní OLE vědět, že **pomoci** nabídky patří do kontejneru a zprávy nabídky odpovídající této nabídky (a její dílčích) by měl směrovat do kontejneru. Je pak kontejneru odpovědnost předávat `WM_INITMENUPOPUP`, **WM_SELECT**, **wm_command –**a další související nabídky zprávy, které patří do objektu část **Nápověda**  nabídky. To se dá udělat pomocí `WM_INITMENU` Vymazat příznak, který sděluje kontejneru, jestli má uživatel přešel do objektu **pomoci** nabídky. Kontejner pak sleduje `WM_MENUSELECT` pro vystupují z libovolnou položku v **pomoci** nabídky, která kontejneru nebyla přidána sám sebe. Na záznam, znamená to uživatel přešel do nabídky k objektu tak, aby kontejneru nastavuje příznak "v nabídce Nápověda objektu" a používá stav tohoto příznaku předávat všechny `WM_MENUSELECT`, `WM_INITMENUPOPUP`, a **wm_command –** zprávy, alespoň na okno objekt. (Při ukončení kontejneru vymaže příznak a poté je zpracovává tyto stejné zprávy sám sebe.) Kontejner by měl použít okno vrácená z objektu **IOleInPlaceActiveObejct::GetWindow** fungovat jako cíl pro tyto zprávy.  
  
 Pokud objekt zjistí nula v šesté elementu **OLEMENUGROUPWIDTHS**, pokračuje podle normální pravidel OLE dokumenty. Tento postup popisuje kontejnery, které jsou součástí **pomoci** a také ty, které nepodporují slučování nabídek.  
  
 Při volání objektu **IOleInPlaceFrame::SetMenu**, než zobrazení sloučené nabídky panelu kontroly kontejneru, jestli **pomoci** nabídky má další dílčí, kromě co má kontejneru Vložit. Pokud ano, kontejneru opustí jeho **pomoci** nabídky v panelu nabídek sloučené. Pokud **pomoci** nabídky nemá další dílčí, dojde k odebrání kontejneru jeho **pomoci** nabídky v panelu nabídek sloučené. Tento postup popisuje objekty, které jsou součástí **pomoci** a také ty, které nepodporují slučování nabídek.  
  
 Nakonec, pokud nastane čas na převod ze strojového kódu v nabídce, objekt odebere vloženého **pomoci** nabídky kromě odebrání dalších vložit nabídky. Když kontejneru odebere jeho nabídky, odebere jeho **pomoci** nabídky kromě jiných nabídky, které se má vložit.  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery pro aktivní dokument](../mfc/active-document-containers.md)

