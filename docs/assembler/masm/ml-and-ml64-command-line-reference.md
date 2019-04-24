---
title: Referenční dokumentace pro použití nástroje ML a ML64 v příkazovém řádku
ms.date: 08/30/2018
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
ms.openlocfilehash: a452bab03e31436ee5dde476117bce8b73c7571f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178108"
---
# <a name="ml-and-ml64-command-line-reference"></a>Referenční dokumentace pro použití nástroje ML a ML64 v příkazovém řádku

Sestaví a odkazuje jeden nebo více zdrojových souborů sestavení jazyka. Možnosti příkazového řádku jsou malá a velká písmena.

Další informace o ml64.exe najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="syntax"></a>Syntaxe

> ML \[ *možnosti*] *filename* \[ \[ *možnosti*] *filename*]
>
> Ml64 v příkazovém \[ *možnosti*] *filename* \[ \[ *možnosti*] *filename*]... \[/link *linkoptions*]

### <a name="parameters"></a>Parametry

*Možnosti*<br/>
Možnosti uvedené v následující tabulce.

|Možnost|Akce|
|------------|------------|
|**/AT**|Umožňuje aplikaci malého modelu paměti podporu. Umožňuje chybové zprávy pro konstrukce kódu, které porušují požadavky na soubory ve formátu .com. Všimněte si, že to není ekvivalentní [. MODEL](../../assembler/masm/dot-model.md) **TINY** směrnice.<br /><br /> Není k dispozici v ml64.exe.|
|**/BL** *název souboru*|Vybere alternativní linkeru.|
|**/c**|Sestaví pouze. Není propojena.|
|**/coff**|Vygeneruje soubor objektu běžné format (COFF) typ objektu modulu. Obecně potřebné pro vývoj jazyk sestavení Win32.<br /><br /> Není k dispozici v ml64.exe.|
|**/Cp**|Zachová případ všechny identifikátory uživatele.|
|**/Cu**|Všechny identifikátory se mapuje na velká písmena (výchozí).<br /><br /> Není k dispozici v ml64.exe.|
|**/Cx**|Zachová veřejného partnerského vztahu a externí symboly v takovém případě.|
|**/D** *symbol*[[=*value*]]|Definuje makra text s daným názvem. Pokud *hodnotu* je chybí, je prázdný. Více tokenů oddělené mezerami musí být uzavřen v uvozovkách.|
|**/EP**|Generuje seznam předem zpracovaný zdroj (odeslané do STDOUT). Zobrazit **/Sf**.|
|**/ ERRORREPORT** [ **NONE** &AMP;#124; **VÝZVY** &AMP;#124; **FRONTY** &AMP;#124; **ODESLAT** ]|Pokud ml.exe nebo ml64.exe selže v době běhu, můžete použít **/errorreport** odesílat informace společnosti Microsoft o tyto vnitřní chyby.<br /><br /> Další informace o **/errorreport**, naleznete v tématu [/errorreport (sestava interními chybami kompilátoru)](../../build/reference/errorreport-report-internal-compiler-errors.md).|
|**/F** *hexnum*|Nastaví velikost do zásobníku *hexnum* bajtů (to je stejný jako **/odkazu/STACK**:*číslo*). Hodnota musí být vyjádřena v šestnáctkové soustavě. Musí být mezera mezi **/F** a *hexnum*.|
|**/FE** *název souboru*|Název spustitelného souboru.|
|**/FL**[[*filename*]]|Generuje seznam deskách kódu. Zobrazit **/Sf**.|
|**/FM**[[*filename*]]|Vytvoří soubor mapy linkeru.|
|**/Fo** *název souboru*|Název souboru objektu. Další informace jsou uvedeny v části poznámky.|
|**/FPi**|Generuje oprava disponují emulátor pro aritmetické operace s plovoucí desetinnou čárkou (pouze smíšeným jazykem).<br /><br /> Není k dispozici v ml64.exe.|
|**/FR**[[*filename*]]|Generuje zdrojový soubor .sbr prohlížeče.|
|**/FR**[[*filename*]]|Generuje vyžaduje rozšířený formát zdrojového souboru .sbr prohlížeče.|
|**/Gc**|Určuje použití stylu až po FORTRAN nebo Pascal funkce volání a konvence vytváření názvů. Stejné jako **možností jazyka: PASCAL**.<br /><br /> Není k dispozici v ml64.exe.|
|**/Gd**|Určuje použití stylu C funkce volání a konvence vytváření názvů. Stejné jako **možností jazyka: C**.<br /><br /> Není k dispozici v ml64.exe.|
|**/GZ**|Určuje použití funkce __stdcall volání a konvence vytváření názvů.  Stejné jako **možností jazyka: STCALL**.<br /><br /> Není k dispozici v ml64.exe.|
|**/H** *číslo*|Externí názvy omezuje počet významných znaků. Výchozí hodnota je 31 znaků.<br /><br /> Není k dispozici v ml64.exe.|
|**/ Help**|Volá QuickHelp nápovědu k ML.|
|**/I** *cesta*|Nastaví cestu k souboru include. Maximálně 10 **/I** možnosti je povoleno.|
|**/nologo**|Potlačí zobrazování zpráv pro úspěšné sestavení.|
|**/ omf**|Vytváří objekt modulu soubor formátu (OMF) typ objektu modulu.  **/ omf** znamená **/c**; ML.exe nepodporuje odkazování omf – objekty.<br /><br /> Není k dispozici v ml64.exe.|
|**/Sa**|Zapne seznam všechny dostupné informace.|
|**/safeseh**|Označí objekt jako buď neobsahující žádné obslužné rutiny výjimky nebo obsahující obslužné rutiny výjimek, které jsou deklarovány pomocí [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> Není k dispozici v ml64.exe.|
|**/Sf**|Přidá soubor výpisu k výpisu první pass.|
|**/Sl** *šířka*|Nastaví šířku čáry v znaky na řádek zdroje. Rozsah je 0 nebo 60 až 255. Výchozí hodnota je 0. Stejné jako [stránky](../../assembler/masm/page.md) šířku.|
|**/Sn**|Při vytváření výpis vypne tabulky symbolů.|
|**/SP** *délku*|Nastaví délku stránky zdroje v řádků na stránce. Rozsah je 0 nebo 10 až 255. Výchozí hodnota je 0. Stejné jako [stránky](../../assembler/masm/page.md) délku.|
|**/Ss** *text*|Určuje text pro výpis zdroje. Stejné jako [TITULEK](../../assembler/masm/subtitle.md) text.|
|**/St** *text*|Určuje název zdrojového seznamu. Stejné jako [název](../../assembler/masm/title.md) text.|
|**/Sx**|Zapne false podmíněné výrazy v seznamu.|
|**/Ta** *název souboru*|Sestaví zdrojového souboru, jehož název nekončí příponou .asm.|
|**/w**|Stejné jako **/W0/WX**.|
|**/W** *úroveň*|Nastaví úroveň pro upozornění, kde *úroveň* = 0, 1, 2 nebo 3.|
|**/WX**|Vrátí kód chyby, pokud se upozornění.|
|**/X**|Ignorujte prostředí cesty zahrnutí.|
|**/Zd**|Generuje informace o číslech řádků v souboru objektů.|
|**/Zf**|Díky veřejné všechny symboly.|
|**/Zi**|Generuje informace CodeView v objektu souboru.|
|**/Zm**|Umožňuje**M510** možnost pro maximální kompatibilitu s MASM 5.1.<br /><br /> Není k dispozici v ml64.exe.|
|**/ Zp**[[*zarovnání*]]|Sbalí struktury na hranici zadaném bajtu. *Zarovnání* může být 1, 2 nebo 4.|
|**/Zs**|Provádí pouze kontrola syntaxe.|
|**/?**|Zobrazí souhrn syntaxe příkazového řádku ML.|

*Název souboru*<br/>
Název souboru.

*linkoptions*<br/>
Možnosti odkazů.  Zobrazit [možnosti Linkeru](../../build/reference/linker-options.md) Další informace.

## <a name="remarks"></a>Poznámky

Některé možnosti příkazového řádku pro použití nástroje ML a ml64 v příkazovém jsou citlivé na umístění. Například protože ML a ml64 v příkazovém může přijmout několik **/c** možnosti, odpovídající **/Fo** možnosti musí být zadán před **/c**. Následující příklad příkazového řádku ukazuje specifikaci souboru objektu pro každý specifikace souboru sestavení:

**ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**

## <a name="environment-variables"></a>Proměnné prostředí

|Proměnná|Popis|
|--------------|-----------------|
|INCLUDE|Určuje cesty pro hledání vložených souborů.|
|ML|Určuje výchozí možnosti příkazového řádku.|
|TMP|Určuje cestu pro dočasné soubory.|

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>
[Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>