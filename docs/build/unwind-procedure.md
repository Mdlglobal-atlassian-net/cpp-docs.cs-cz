---
title: Unwind – procedura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 82c5d0ca-70be-4d1a-a306-bfe01c29159f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 294353baf8c15818ba836bd3093226a78aa6e44c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700651"
---
# <a name="unwind-procedure"></a>Unwind – procedura

Unwind kódu je seřazen v sestupném pořadí. Když dojde k výjimce, úplný kontext uložený v kontextového záznamu v operačním systému. Odeslání logiky výjimka je následně vyvolány, která provádí následující kroky k nalezení obslužné rutiny výjimky.

1. Aktuální RIP uložené v záznamu o kontextu slouží k vyhledání položky v tabulce runtime, která popisuje aktuální funkci (nebo část funkce, v případě zřetězených položek UNWIND_INFO).

1. Pokud se nenajde žádný záznam tabulky funkcí, pak je ve funkci typu list a RSP bude adresovat přímo návratový ukazatel. Vrácené ukazatel na [RSP] je uložen v rámci aktualizované, simulované RSP je zvýšen o 8 a opakovat krok 1.

1. Pokud se najde záznam tabulky funkcí, RIP může nacházet ve třech oblastech) v epilogu, (b) v prologu nebo c) v kódu, který může být pokryté komponentami obslužné rutiny výjimky.

   - Case) Pokud RIP je v rámci epilogu, pak opouští funkce ovládacího prvku, může být žádná obslužná rutina výjimky, který je přidružený k této výjimky pro tuto funkci a efekty epilogu musí být nadále výpočetního kontextu volající funkce. Chcete-li zjistit, pokud je v rámci epilogu datový proud kódu z RIP RIP na je zkontrolován. Pokud tento datový proud kódu je možné přiřadit ke konci části legitimní epilogu pak je v epilog a zbývající část epilogu simulujeme, s kontextového záznamu, aktualizovat, protože každou instrukci jsou zpracovávána. Potom se opakuje kroku 1.

   - Případ b) Pokud RIP leží v prologu, nemá -li ovládací prvek není vložené funkce, může být žádná obslužná rutina výjimky, který je přidružený k této výjimky pro tuto funkci a efekty prologu musí vrátit zpět k výpočetním kontextu volající funkce. RIP se v prologu, pokud vzdálenost od zahájení funkce do RIP je menší než nebo roven velikosti prologu kódována unwind info. Účinky prologu jsou odděleny prohledávání vpřed prostřednictvím unwind kódů pro první položku s posunem menší než nebo rovný posunu RIP od samého začátku funkce a pak vracením všechny zbývající položky v kódu unwind. Krok 1 se pak opakuje.

   - Případu c), pokud RIP se nenachází v prologu nebo epilogu a funkce má obslužné rutiny výjimek (UNW_FLAG_EHANDLER nastavuje), pak volá obslužná rutina pro konkrétní jazyk. Obslužná rutina vyhledá svoje data a volání funkce jako odpovídající filtru. Obslužná rutina pro konkrétní jazyk může vrátit, že výjimka byla zpracována nebo, že má být pokračování hledání. Unwind ho také můžete spustit přímo.

1. Pokud obslužná rutina pro konkrétní jazyk vrátí zpracované stav, pak se pokračuje pomocí původního záznamu o kontextu.

1. Pokud neexistuje žádná obslužná rutina konkrétní jazyk nebo obslužná rutina vrátí stav "pokračuje v hledání", musí být oddělen stav volajícího kontextového záznamu. Toho lze dosáhnout zpracování všech prvků pole kód unwind vracením každého. Krok 1 se pak opakuje.

Při řetězení unwind info je zahrnuta, stále postupovali podle těchto základních kroků. Jediným rozdílem je, že při procházení unwind kódu k provedení operace unwind prologu efekty, jakmile je dosaženo konce pole, je nadřazená unwind informace pak propojen a šel celý unwind kódu můžete najít zde. Toto propojení pokračuje, dokud přicházejících u unwind informace bez příznaku UNW_CHAINED_INFO a dokončení walking jeho unwind kódu.

Nejmenší sadu unwind dat je 8 bajtů. To představuje funkci, která jen přidělených 128 bajtů zásobníku nebo méně a může být uložen jeden stálé registr. Toto je také velikost zřetězené struktury unwind informace prologu nulové délky s žádné kódy unwind.

## <a name="see-also"></a>Viz také

[Zpracování výjimek (x64)](../build/exception-handling-x64.md)