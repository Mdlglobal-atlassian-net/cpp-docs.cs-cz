---
title: Chyba modulu C runtime R6028
ms.date: 11/04/2016
f1_keywords:
- R6028
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
ms.openlocfilehash: 1c165b7c9351e34ef6316962cd90663f2b6152ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197129"
---
# <a name="c-runtime-error-r6028"></a>Chyba modulu C runtime R6028

Nelze inicializovat haldu

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace se vypnula, protože má problém interní paměti. Tato chyba má mnoho možných důvodů, ale často je způsobena extrémně nedostatkem paměti, chybou v programu nebo vadnými hardwarovými ovladači.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartujte počítač pro uvolnění paměti.
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Pokud aplikace pracovala před poslední instalací jiné aplikace nebo ovladače, odeberte novou aplikaci nebo ovladač pomocí stránky **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** a zkuste aplikaci znovu.
> - Aktualizace softwaru a ovladačů najdete na webu dodavatele hardwaru nebo v **web Windows Update** v **Ovládacích panelech** .
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dojde, když se operačnímu systému nepodaří vytvořit fond paměti pro aplikace. Konkrétně modul runtime jazyka C (CRT) volal funkci Win32 `HeapCreate`, která vrátila hodnotu NULL indikující selhání.

Pokud k této chybě dojde během spouštění aplikace, nemusí být systém schopen splnit požadavky haldy, protože jsou načteny vadné ovladače. Pomocí služby Windows Update nebo na webu dodavatele hardwaru vyhledejte aktualizované ovladače.
