---
title: Spuštění příkazu NMAKE
description: Referenční příručka k možnostem příkazového řádku Microsoft NMAKE
ms.date: 02/09/2020
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: bfada33a89c04d25bf7444cbf3b1e7ef3ed44385
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856925"
---
# <a name="running-nmake"></a>Spuštění příkazu NMAKE

## <a name="syntax"></a>Syntaxe

> **NMAKE** [*možnost* ...] [*makra* ...] [*cíle* ...] [ **\@** _příkazového souboru_ ...]

## <a name="remarks"></a>Poznámky

NMAKE sestaví pouze zadané *cíle* nebo, pokud není zadán, první cíl v souboru pravidel. První cíl souboru pravidel může být [pseudotarget](description-blocks.md#pseudotargets) , který vytváří další cíle. Nástroj NMAKE používá soubory pravidel zadané s **parametrem/f**, nebo pokud **parametr/f** není zadán, soubor pravidel v aktuálním adresáři. Pokud není zadán žádný soubor pravidel, používá odvozená pravidla pro sestavení *cílů*příkazového řádku.

Textový soubor *s příkazovým souborem* (nebo soubor odezvy) obsahuje vstup z příkazového řádku. Další vstup může předcházet nebo sledovat \@*příkazového souboru*. Cesta je povolena. V *příkazovém souboru*jsou zalomení řádků považovány za mezery. Definice maker uzavřete do uvozovek, pokud obsahují mezery.

## <a name="nmake-options"></a>NMAKE – možnosti

Možnosti nástroje NMAKE jsou popsány v následující tabulce. Možnosti předcházejí buď lomítko (`/`), nebo pomlčkou (`-`), a nerozlišují se malá a velká písmena. Pomocí [`!CMDSWITCHES`](makefile-preprocessing-directives.md) můžete změnit nastavení možností v souboru pravidel nebo v souboru Tools. ini.

| Možnost | Účel |
| ------------ | ------------- |
| **Parametr** | Vynutí sestavení všech vyhodnocených cílů, a to i v případě, že nejsou v porovnání s závislými. Nenutí sestavení nesouvisejících cílů. |
| **/B** | Vynutí sestavení i v případě, že jsou časová razítka shodná. Doporučuje se jenom pro rychlé systémy (rozlišení dvou sekund nebo i méně). |
| **/C** | Potlačí výchozí výstup, včetně méně závažné chyby nebo varování, časová razítka a Copyright zprávy NMAKE. Potlačí upozornění vydaná v **/k**. |
| **Parametr** | Zobrazí časová razítka každého vyhodnoceného cíle a závislého a zprávu, pokud cíl neexistuje. Užitečné s parametrem **/p** pro ladění souboru pravidel. Pomocí `!CMDSWITCHES` nastavte nebo zrušte zaškrtnutí políčka **/d** pro část souboru pravidel. |
| **/E** | Způsobí, že proměnné prostředí přepíší definice makra souboru pravidel. |
| **/errorreport** [ **žádné** &#124; &#124; **odeslání** **fronty** **výzvy** &#124; ] | Zastaralé Nastavení [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) řízení sestav. |
| *Název souboru* /f | Určuje *název souboru* jako soubor pravidel. *Název souboru*může předcházet mezera nebo tabulátory. U každého souboru pravidel zadejte **/f** . Chcete-li zadat soubor pravidel ze standardního vstupu, zadejte pomlčku (`-`) pro *název souboru*a ukončete vstup klávesnice buď pomocí **klávesy F6** , nebo **kombinací kláves CTRL + Z**. |
| **/G** | Zobrazuje soubory pravidel zahrnuté v direktivě `!INCLUDE`. Další informace naleznete v tématu [direktivy předběžného zpracování souboru pravidel](makefile-preprocessing-directives.md). |
| **/Help**, **/?** | Zobrazí stručný souhrn syntaxe příkazového řádku NMAKE. |
| **Parametr** | Ignoruje ukončovací kódy ze všech příkazů. Chcete-li nastavit nebo vymazat parametr **/i** pro část souboru pravidel, použijte `!CMDSWITCHES`. Chcete-li ignorovat ukončovací kódy pro část souboru pravidel, použijte modifikátor příkazu pomlčky (`-`) nebo [`.IGNORE`](dot-directives.md). Potlačí **/k** , pokud jsou zadány obě. |
| **/K** | Pokračuje v vytváření nesouvisejících závislostí, pokud příkaz vrátí chybu. Také vydá upozornění a vrátí ukončovací kód 1. Ve výchozím nastavení se NMAKE zastaví, pokud libovolný příkaz vrátí nenulový ukončovací kód. Upozornění z **/k** se potlačí pomocí **/c**; **/I** potlačí **/k** , pokud jsou zadány obě. |
| **N** | Zobrazí, ale neprovede příkazy. příkazy předběžného zpracování jsou spuštěny. Nezobrazuje příkazy v rekurzivních voláních NMAKE. Užitečné pro ladění souborů pravidel a kontrolu časových razítek. Chcete-li nastavit nebo zrušit volbu **/n** pro část souboru pravidel, použijte `!CMDSWITCHES`. |
| **/NOLOGO** | Potlačí zprávu o autorských právech NMAKE. |
| **/P** | Zobrazí informace (definice maker, odvozená pravidla, cíle, [`.SUFFIXES`](dot-directives.md) seznam) do standardního výstupu a potom spustí sestavení. Pokud neexistuje žádný soubor pravidel ani cíl příkazového řádku, zobrazí pouze informace. Použijte s **parametrem/d** k ladění souboru pravidel. |
| **Parametr** | Kontroluje časová razítka cílů; nespustí sestavení. Vrátí nulový ukončovací kód, pokud jsou všechny cíle aktuální, a nenulový ukončovací kód, pokud je nějaký cíl zastaralý. Příkazy předběžného zpracování jsou spuštěny. Užitečné při spuštění NMAKE ze souboru Batch. |
| **/R** | Vymaže seznam `.SUFFIXES` a ignoruje odvozená pravidla a makra definovaná v souboru Tools. ini nebo předdefinované. |
| **Parametr** | Potlačí zobrazení provedených příkazů. Pro potlačení zobrazení v části souboru pravidel použijte modifikátor příkazu **\@** nebo [`.SILENT`](dot-directives.md). Chcete-li nastavit nebo vymazat **/s** pro část souboru pravidel, použijte `!CMDSWITCHES`. |
| **Parametr** | Aktualizuje časová razítka cílů příkazového řádku (nebo prvního cíle souboru pravidel) a provede příkazy předběžného zpracování, ale sestavení nespustí. |
| **Přepínač** | Musí se používat ve spojení s **/n**. Vypíše vložené soubory NMAKE tak, aby výstup **/n** mohl být použit jako dávkový soubor. |
| **/X** *název souboru* | Místo standardní chyby pošle chybový výstup na *název souboru* . *Název souboru*může předcházet mezera nebo tabulátory. Chcete-li odeslat chybový výstup do standardního výstupu, zadejte pomlčku (`-`) pro *název souboru*. Nemá vliv na výstup z příkazů na standardní chybu. |
| **/Y** | Zakáže odvození pravidel v dávkovém režimu. Pokud je vybrána tato možnost, jsou všechna odvozená pravidla v dávkovém režimu považována za běžná odvozená pravidla. |

## <a name="toolsini-and-nmake"></a>Tools.ini a příkaz NMAKE

Nástroj NMAKE čte nástroje. ini před čtením souborů pravidel, pokud se nepoužije **/r** . V aktuálním adresáři vyhledává nástroje Tools. ini a potom v adresáři určeném proměnnou prostředí INIT. Oddíl nastavení nástroje NMAKE v inicializačním souboru začíná na `[NMAKE]` a může obsahovat jakékoli informace o souboru pravidel. Zadejte komentář na samostatné řádky začínající znakem čísla (`#`).

## <a name="exit-codes-from-nmake"></a>Kódy ukončení příkazu NMAKE

NMAKE vrátí následující ukončovací kódy:

| Kód | Význam |
| ---------- | ------------- |
| 0 | Žádná chyba (možná upozornění) |
| 1 | Neúplné sestavení (vydáno pouze při použití **/k** ) |
| 2 | Chyba programu, pravděpodobně způsobená jedním z těchto problémů:<br /> – Chyba syntaxe v souboru pravidel<br /> – Chyba nebo ukončení kódu z příkazu<br /> – Přerušení uživatelem |
| 4 | Systémová chyba – nedostatek paměti |
| 255 | Cíl není aktuální (vydáno pouze při použití **/q** ). |

## <a name="see-also"></a>Viz také

[NMAKE – referenční zdroje](nmake-reference.md)
