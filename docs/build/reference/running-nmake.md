---
title: Spuštění příkazu NMAKE
ms.date: 08/11/2019
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: bc274190b64d5340aaac5de594931d4a5333a8c0
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980492"
---
# <a name="running-nmake"></a>Spuštění příkazu NMAKE

## <a name="syntax"></a>Syntaxe

> **NMAKE** [*parametr* ...] [*makra* ...] [*cíle* ...] [ **\@** _Command-File_ ...]

## <a name="remarks"></a>Poznámky

NMAKE sestaví pouze zadané *cíle* nebo, pokud není zadán, první cíl v souboru pravidel. První cíl souboru pravidel může být [pseudotarget](pseudotargets.md) , který vytváří další cíle. Nástroj NMAKE používá soubory pravidel zadané s **parametrem/f**, nebo pokud **parametr/f** není zadán, soubor pravidel v aktuálním adresáři. Pokud není zadán žádný soubor pravidel, používá odvozená pravidla pro sestavení *cílů*příkazového řádku.

Textový soubor *s příkazovým souborem* (nebo soubor odezvy) obsahuje vstup z příkazového řádku. Další vstup může předcházet nebo \@následovat po *příkazovém souboru*. Cesta je povolena. V *příkazovém souboru*jsou zalomení řádků považovány za mezery. Definice maker uzavřete do uvozovek, pokud obsahují mezery.

## <a name="nmake-options"></a>NMAKE – možnosti

Možnosti nástroje NMAKE jsou popsány v následující tabulce. Možnosti předcházejí buď lomítko (`/`), nebo pomlčkou (`-`), a nerozlišují se malá a velká písmena. Slouží [`!CMDSWITCHES`](makefile-preprocessing-directives.md) ke změně nastavení možností v souboru pravidel nebo v souboru Tools. ini.

| Možnost | Účel |
| ------------ | ------------- |
| **/A** | Vynutí sestavení všech vyhodnocených cílů, a to i v případě, že nejsou v porovnání s závislými. Nenutí sestavení nesouvisejících cílů. |
| **/B** | Vynutí sestavení i v případě, že jsou časová razítka shodná. Doporučuje se jenom pro velmi rychlé systémy (rozlišení dvou sekund nebo i méně). |
| **/C** | Potlačí výchozí výstup, včetně méně závažné chyby nebo varování, časová razítka a Copyright zprávy NMAKE. Potlačí upozornění vydaná v **/k**. |
| **/D** | Zobrazí časová razítka každého vyhodnoceného cíle a závislého a zprávu, pokud cíl neexistuje. Užitečné s parametrem **/p** pro ladění souboru pravidel. Použijte `!CMDSWITCHES` k nastavení nebo zrušení pro část souboru pravidel **/d** . |
| **/E** | Způsobí, že proměnné prostředí přepíší definice makra souboru pravidel. |
| **/ERRORREPORT** [ **ŽÁDNÉ** &#124; **ODESLÁNÍ** **DO FRONTY** &#124; **VÝZVY** &#124; ] | Pokud soubor NMAKE. exe během běhu selhává, můžete použít **/errorreport** k odeslání informací společnosti Microsoft o těchto interních chybách.<br /><br /> Další informace najdete v tématu [/errorreport (hlášení chyb interních kompilátorů)](errorreport-report-internal-compiler-errors.md). |
| **/F** *název souboru* | Určuje *název souboru* jako soubor pravidel. *Název souboru*může předcházet mezera nebo tabulátory. U každého souboru pravidel zadejte **/f** . Chcete-li zadat soubor pravidel ze standardního vstupu, zadejte`-`pomlčku () pro *název souboru*a ukončete vstup klávesnice buď pomocí **klávesy F6** , nebo **kombinací kláves CTRL + Z**. |
| **/G** | Zobrazuje soubory pravidel zahrnuté `!INCLUDE` v direktivě. Další informace naleznete v tématu [direktivy předběžného zpracování souboru pravidel](makefile-preprocessing-directives.md). |
| **/HELP**, **/?** | Zobrazí stručný souhrn syntaxe příkazového řádku NMAKE. |
| **/I** | Ignoruje ukončovací kódy ze všech příkazů. Chcete-li nastavit nebo vymazat **/i** pro část souboru pravidel, `!CMDSWITCHES`použijte. Chcete-li ignorovat ukončovací kódy pro část souboru pravidel, použijte modifikátor příkazu`-`spojovník () nebo [`.IGNORE`](dot-directives.md). Potlačí **/k** , pokud jsou zadány obě. |
| **/K** | Pokračuje v vytváření nesouvisejících závislostí, pokud příkaz vrátí chybu. Také vydá upozornění a vrátí ukončovací kód 1. Ve výchozím nastavení se NMAKE zastaví, pokud libovolný příkaz vrátí nenulový ukončovací kód. Upozornění z **/k** se potlačí pomocí **/c**; **/I** potlačí **/k** , pokud jsou zadány obě. |
| **N** | Zobrazí, ale neprovede příkazy. příkazy předběžného zpracování jsou spuštěny. Nezobrazuje příkazy v rekurzivních voláních NMAKE. Užitečné pro ladění souborů pravidel a kontrolu časových razítek. Chcete-li nastavit nebo zrušit volbu **/n** pro část souboru pravidel `!CMDSWITCHES`, použijte. |
| **/NOLOGO** | Potlačí zprávu o autorských právech NMAKE. |
| **/P** | Zobrazí informace (definice maker, odvozená pravidla, cíle, [`.SUFFIXES`](dot-directives.md) seznam) do standardního výstupu a potom spustí sestavení. Pokud neexistuje žádný soubor pravidel ani cíl příkazového řádku, zobrazí pouze informace. Použijte s **parametrem/d** k ladění souboru pravidel. |
| **PARAMETR** | Kontroluje časová razítka cílů; nespustí sestavení. Vrátí nulový ukončovací kód, pokud jsou všechny cíle aktuální, a nenulový ukončovací kód, pokud je nějaký cíl zastaralý. Příkazy předběžného zpracování jsou spuštěny. Užitečné při spuštění NMAKE ze souboru Batch. |
| **/R** | `.SUFFIXES` Vymaže seznam a ignoruje odvozená pravidla a makra, která jsou definovaná v souboru Tools. ini nebo jsou předdefinované. |
| **PARAMETR** | Potlačí zobrazení provedených příkazů. Pro potlačení zobrazení v části souboru pravidel použijte **\@** modifikátor příkazu nebo. [`.SILENT`](dot-directives.md) Chcete-li nastavit nebo vymazat **/s** pro část souboru pravidel, `!CMDSWITCHES`použijte. |
| **/T** | Aktualizuje časová razítka cílů příkazového řádku (nebo prvního cíle souboru pravidel) a provede příkazy předběžného zpracování, ale sestavení nespustí. |
| **/U** | Musí se používat ve spojení s **/n**. Vypíše vložené soubory NMAKE tak, aby výstup **/n** mohl být použit jako dávkový soubor. |
| **/X** *název souboru* | Místo standardní chyby pošle chybový výstup na *název souboru* . *Název souboru*může předcházet mezera nebo tabulátory. Chcete-li odeslat chybový výstup do standardního výstupu, zadejte pomlčku (`-`) pro *název souboru*. Nemá vliv na výstup z příkazů na standardní chybu. |
| **/Y** | Zakáže odvození pravidel v dávkovém režimu. Pokud je vybrána tato možnost, jsou všechna odvozená pravidla v dávkovém režimu považována za běžná odvozená pravidla. |

## <a name="toolsini-and-nmake"></a>Tools.ini a příkaz NMAKE

Nástroj NMAKE čte nástroje. ini před čtením souborů pravidel, pokud se nepoužije **/r** . V aktuálním adresáři vyhledává nástroje Tools. ini a potom v adresáři určeném proměnnou prostředí INIT. Oddíl pro nastavení nástroje NMAKE v inicializačním souboru začíná `[NMAKE]` na a může obsahovat jakékoli informace o souboru pravidel. Zadejte komentář na samostatné řádky začínající znakem čísla (`#`).

## <a name="exit-codes-from-nmake"></a>Kódy ukončení příkazu NMAKE

NMAKE vrátí následující ukončovací kódy:

| Kód | Význam |
| ---------- | ------------- |
| 0 | Žádná chyba (možná upozornění) |
| 1 | Neúplné sestavení (vydáno pouze při použití **/k** ) |
| 2 | Chyba programu, pravděpodobně způsobená jedním z těchto problémů:<br /> – Chyba syntaxe v souboru pravidel<br /> – Chyba nebo ukončení kódu z příkazu<br /> – Přerušení uživatelem |
| 4 | Systémová chyba – nedostatek paměti |
| 255 | Cíl není aktuální (vydáno pouze při použití **/q** ). |

## <a name="see-also"></a>Viz také:

[NMAKE – referenční zdroje](nmake-reference.md)
