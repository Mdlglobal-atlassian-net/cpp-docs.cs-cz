---
title: Referenční dokumentace pro použití nástroje ML a ML64 v příkazovém řádku
ms.date: 12/17/2019
f1_keywords:
- ML
helpviewer_keywords:
- /W* MASM compiler option
- /c MASM compiler option
- /EP MASM compiler option
- /Fe MASM compiler option
- /Zp MASM compiler option
- /AT MASM compiler option
- /Zm MASM compiler option
- /Sf MASM compiler option
- /Sp MASM compiler option
- /w MASM compiler option
- /Fl MASM compiler option
- /coff MASM compiler option
- /St MASM compiler option
- /Cx MASM compiler option
- /Sl MASM compiler option
- /Cu MASM compiler option
- MASM (Microsoft Macro Assembler), ML command-line reference
- /FPi MASM compiler option
- /Zf MASM compiler option
- ML environment variable
- /Fr MASM compiler option
- /help MASM compiler option
- /Sa MASM compiler option
- /Zd MASM compiler option
- /I MASM compiler option
- /? MASM compiler option
- /Bl MASM compiler option
- /Fm MASM compiler option
- /Fo MASM compiler option
- command-line reference [ML]
- /Sn MASM compiler option
- /Gd MASM compiler option
- /D* MASM compiler option
- environment variables, ML
- /Gc MASM compiler option
- /F* MASM compiler option
- /Sc MASM compiler option
- /H MASM compiler option
- /Zs MASM compiler option
- /omf MASM compiler option
- /Sg MASM compiler option
- /Cp MASM compiler option
- /Zi MASM compiler option
- /nologo MASM compiler option
- /Sx MASM compiler option
- /WX MASM compiler option
- /Ss MASM compiler option
- command line, reference [ML]
- /Ta MASM compiler option
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
ms.openlocfilehash: 77385317ab7f90a646b7f552e471d0f434e72bfb
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317159"
---
# <a name="ml-and-ml64-command-line-reference"></a>Referenční dokumentace pro použití nástroje ML a ML64 v příkazovém řádku

Sestaví a propojuje jeden nebo více zdrojových souborů jazyka sestavení. V parametrech příkazového řádku jsou rozlišována velká a malá písmena.

Další informace o ml64. exe naleznete v tématu [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="syntax"></a>Syntaxe

> ML \[*Možnosti*] *filename* \[ \[*Možnosti*] *filename*]
>
> ML64 \[*Možnosti*] *filename* \[ \[*Možnosti*] *filename*]... \[/Link *linkOptions*]

### <a name="parameters"></a>Parametry

*možnosti*\
Možnosti uvedené v následující tabulce.

|Možnost|Akce|
|------------|------------|
|**/AT**|Povolí podporu modelu s malými paměťmi. Povoluje chybové zprávy pro konstrukce kódu, které porušují požadavky na soubory formátu. com. Všimněte si, že se nejedná o ekvivalent [. MODELem](dot-model.md) **nepatrné** direktivy.<br /><br /> Není k dispozici v souboru ml64. exe.|
|*Název souboru* /BL|Vybere alternativní linker.|
|**/c**|Pouze sestavuje. Neodkazuje na.|
|**/coff**|Generuje typ objektu Common Object File Format (COFF). Obecně se vyžaduje pro vývoj jazyka pro sestavení Win32.<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/Cp**|Zachovává případ všech uživatelských identifikátorů.|
|**/Cu**|Mapuje všechny identifikátory na velká písmena (výchozí).<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/Cx**|Zachová velká a externí písma v symbolech Public a extern.|
|**/D** *symbol*⟦ =*Value*⟧|Definuje textové makro se zadaným názvem. Pokud *hodnota* chybí, je prázdná. Více tokenů oddělených mezerami musí být uzavřeny v uvozovkách.|
|**/EP**|Vygeneruje předzpracovaný výpis zdrojového kódu (odesláno do STDOUT). Viz **/SF**.|
|**/errorreport** [ **žádné** &#124; &#124; **odeslání** **fronty** **výzvy** &#124; ]|Pokud se soubor ml. exe nebo ml64. exe v době běhu nezdařil, můžete použít **/errorreport** k odeslání informací společnosti Microsoft o těchto interních chybách.<br /><br /> Další informace o **/errorreport**najdete v tématu [/errorreport (sestava chyb interních kompilátorů)](../../build/reference/errorreport-report-internal-compiler-errors.md).|
|**/F** *hexnum*|Nastaví velikost zásobníku na *hexnum* bajtů (Toto je stejné jako **/Link/Stack**:*Number*). Hodnota musí být vyjádřena v šestnáctkovém zápisu. Mezi **/f** a *hexnum*musí být mezera.|
|*Název souboru* /FE|Pojmenuje spustitelný soubor.|
|**/FL**⟦*název_souboru*⟧|Vygeneruje sestavený výpis kódu. Viz **/SF**.|
|**/FM**⟦*název_souboru*⟧|Vytvoří soubor mapy linkeru.|
|**/FO** *název souboru*|Pojmenuje soubor objektu. Další informace najdete v části poznámky.|
|**/FPi**|Vygeneruje opravy emulátoru pro aritmetické operace s plovoucí desetinnou čárkou (jenom smíšený jazyk).<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/Fr**⟦*název_souboru*⟧|Vygeneruje zdrojový soubor Browser. sbr.|
|**/Fr**⟦*název_souboru*⟧|Vygeneruje rozšířenou formu zdrojového souboru Browser. sbr.|
|**/Gc**|Určuje použití konvencí volání a názvů funkcí FORTRAN nebo Pascal. Stejné jako **jazyk možnosti: Pascal**.<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/Gd**|Určuje použití konvencí volání a názvů funkcí ve stylu jazyka C. Stejné jako **jazyk možnosti: C**.<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/GZ**|Určuje použití __stdcall volání funkcí a konvence pojmenování.  Stejný jako **jazyk možnosti: STCALL**.<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/H** – *číslo*|Omezí externí názvy na číselné znaky. Výchozí hodnota je 31 znaků.<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/ Help**|Zavolá QuickHelp pro nápovědu o ML.|
|**/I** *cesta*|Nastaví cestu pro soubor include. Povolený je maximálně 10 **/i** možností.|
|**/nologo**|Potlačí zprávy pro úspěšné sestavení.|
|**/omf**|Generuje typ souboru modulu objektu (OMF).  **/OMF** implikuje **/c**; Soubor ML. exe nepodporuje propojování objektů OMF.<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/Sa**|Zapne výpis všech dostupných informací.|
|**/safeseh**|Označí objekt jako buď neobsahuje žádné obslužné rutiny výjimek, nebo obsahuje obslužné rutiny výjimek, které jsou deklarovány pomocí [. SAFESEH](dot-safeseh.md).<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/Sf**|Přidá seznam první předání do výpisu souboru.|
|**/SL** *Šířka*|Nastaví tloušťku čáry zdrojového výpisu znaků na řádek. Rozsah je 60 až 255 nebo 0. Výchozí hodnota je 0. Stejné jako šířka [stránky](page.md) .|
|**/Sn**|Vypne tabulku symbolů při vytváření výpisu.|
|*Délka* /SP|Nastaví délku stránky výpisu zdrojového kódu v řádcích na stránku. Rozsah je 10 až 255 nebo 0. Výchozí hodnota je 0. Stejné jako délka [stránky](page.md) .|
|**/Ss** *text*|Určuje text pro výpis zdrojového kódu. Stejné jako text [podnadpisu](subtitle.md) .|
|**/St** *text*|Určuje název zdrojového výpisu. Totéž jako text [nadpisu](title.md) .|
|**/Sx**|Zapne v výpisu nepravdivé podmíněné výčty.|
|*Název souboru* /ta|Sestaví zdrojový soubor, jehož název nekončí příponou. asm.|
|**/w**|Stejné jako **/W0/WX**.|
|**/W** *úroveň*|Nastaví úroveň upozornění, kde *Level* = 0, 1, 2 nebo 3.|
|**/WX**|Pokud jsou vygenerována upozornění, vrátí kód chyby.|
|**/X**|Ignorovat cestu k prostředí INCLUDE|
|**/Zd**|Generuje informace o číslech řádků v souboru objektu.|
|**/Zf**|Zpřístupní všechny symboly jako veřejné.|
|**/Zi**|Generuje informace CodeView v souboru objektu.|
|**/Zm**|Povolí možnost**M510** pro maximální kompatibilitu s MASM 5,1.<br /><br /> Není k dispozici v souboru ml64. exe.|
|**/Zp***Zarovnání*⟦ na ⟧|Sbalí struktury na zadané hranici bajtů. *Zarovnání* může být 1, 2 nebo 4.|
|**/Zs**|Provede pouze kontrolu syntaxe.|
|**/?**|Zobrazí souhrn syntaxe příkazového řádku ML.|

*název souboru*\
Název souboru

*linkoptions*\
Možnosti propojení.  Další informace najdete v tématu [Možnosti linkeru](../../build/reference/linker-options.md) .

## <a name="remarks"></a>Poznámky

Některé možnosti příkazového řádku pro ML a ML64 jsou citlivé na umístění. Například vzhledem k tomu, že ML a ML64 můžou přijmout několik možností **/c** , musí být před **/c**zadány všechny odpovídající možnosti **/FO** . Následující příklad příkazového řádku ukazuje specifikace souboru objektu pro každou specifikaci souboru sestavení:

**ml. exe/FO a1. obj/c a. asm/FO B1. obj/c b. asm**

## <a name="environment-variables"></a>Proměnné prostředí

|Proměnná|Popis|
|--------------|-----------------|
|INCLUDE|Určuje cestu hledání souborů zahrnutí.|
|ML|Určuje výchozí možnosti příkazového řádku.|
|TMP|Určuje cestu pro dočasné soubory.|

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)\
[Microsoft Macro Assembler – referenční dokumentace](microsoft-macro-assembler-reference.md)
