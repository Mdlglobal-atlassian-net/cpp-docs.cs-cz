---
title: "Referenční dokumentace ML a ml64 v příkazovém řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ML
dev_langs: C++
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
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0cc09c716e8867c03147a28e6c0eb7d4fc844937
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-and-ml64-command-line-reference"></a>Referenční dokumentace pro použití nástroje ML a ML64 v příkazovém řádku
Sestaví a odkazuje jeden nebo více zdrojových souborů jazyka sestavení. Možnosti příkazového řádku jsou velká a malá písmena.  
  
 Další informace o ml64.exe najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### <a name="parameters"></a>Parametry  
 `options`  
 Možnosti uvedené v následující tabulce.  
  
|Možnost|Akce|  
|------------|------------|  
|**/AT**|Umožňuje podporu malá velikost paměti modelu. Umožňuje chybové zprávy pro konstrukce kódu, které porušují požadavky na soubory ve formátu .com. Všimněte si, že to není ekvivalentní [. MODEL](../../assembler/masm/dot-model.md) **velmi malé** – direktiva.<br /><br /> Není k dispozici v ml64.exe.|  
|**/BL**`filename`|Vybere alternativní linkeru.|  
|**/c**|Sestaví jenom. Neobsahuje odkazy.|  
|**/ COFF**|Generuje soubor objekt běžný formát (COFF) typ objektu modulu. Obvykle vyžaduje pro vývoj Win32 jazyk sestavení.<br /><br /> Není k dispozici v ml64.exe.|  
|**/CP**|Zachovává malá všechny identifikátory uživatele.|  
|**/Cu**|Všechny identifikátory mapuje na velká písmena (výchozí).<br /><br /> Není k dispozici v ml64.exe.|  
|**/CX**|Veřejné a extern symboly v takovém případě se zachovají.|  
|**/D** `symbol`[[=`value`]]|Definuje text makro s daným názvem. Pokud `value` je chybí, je prázdný. Více tokeny oddělené mezerami musí být uzavřena v uvozovkách.|  
|**/EP**|Generuje seznam předběžně zpracované zdroje (Odeslat do STDOUT). V tématu **/Sf**.|  
|**/ ERRORREPORT** [ **NONE** &#124; **VÝZVA** &#124; **FRONTY** &#124; **ODESLAT** ]|Pokud ml.exe nebo ml64.exe selže za běhu, můžete použít **/errorreport** odesílat informace společnosti Microsoft o tyto interní chyby.<br /><br /> Další informace o **/errorreport**, najdete v části [/errorreport (sestava interními chybami kompilátoru)](../../build/reference/errorreport-report-internal-compiler-errors.md).|  
|**/F**`hexnum`|Velikost zásobníku sady `hexnum` bajtů (je to stejné nastavení jako **/odkaz/zásobníku**:`number`). Hodnota musí být vyjádřena v šestnáctkové soustavě. Musí být mezery mezi **/F** a `hexnum`.|  
|**/FE**`filename`|Názvy spustitelný soubor.|  
|**/FL**[[`filename`]]|Generuje výpisu sestavený kódu. V tématu **/Sf**.|  
|**/FM**[[`filename`]]|Vytvoří soubor linkeru mapy.|  
|**/Fo**`filename`|Názvy soubor objektu. Další informace jsou uvedeny v části poznámky.|  
|**/ FPi**|Generuje emulátoru opravu ups pro aritmetické s plovoucí desetinnou čárkou (pouze smíšený jazyk).<br /><br /> Není k dispozici v ml64.exe.|  
|**/FR**[[`filename`]]|Generuje zdrojového souboru .sbr prohlížeče.|  
|**/FR**[[`filename`]]|Generuje rozšířené formu zdrojového souboru .sbr prohlížeče.|  
|**/GC**|Určuje použití funkce FORTRAN nebo Pascal styl volání a konvence vytváření názvů. Stejné jako **možnost jazyk: PASCAL**.<br /><br /> Není k dispozici v ml64.exe.|  
|**/GD**|Určuje použití funkce C-style volání a konvence vytváření názvů. Stejné jako **možnost jazyk: C**.<br /><br /> Není k dispozici v ml64.exe.|  
|**/GZ**|Určuje použití funkce __stdcall volání a konvence vytváření názvů.  Stejné jako **možnost jazyk: STCALL**.<br /><br /> Není k dispozici v ml64.exe.|  
|**/H**`number`|Externí názvy omezuje na číslo důležité znaky. Výchozí nastavení je 31 znaků.<br /><br /> Není k dispozici v ml64.exe.|  
|**/ Help**|Nápovědu k ML volá QuickHelp.|  
|**/I**`pathname`|Nastaví cesta k souboru zahrnout. Maximálně 10 **/I** povoleny možnosti.|  
|**/ nologo**|Potlačí zprávy pro úspěšné sestavení.|  
|**/ omf**|Generuje objektu modulu soubor formátu (OMF) typu objektu modulu.  **/ omf** znamená **/c**; ML.exe nepodporuje propojení OMF objektů.<br /><br /> Není k dispozici v ml64.exe.|  
|**/SA**|Zapne seznam všechny dostupné informace.|  
|**/ SAFESEH**|Označí objekt jako obsahující žádné obslužné rutiny výjimek nebo obsahující obslužné rutiny výjimek, které jsou deklarovány s [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> Není k dispozici v ml64.exe.|  
|**/SF**|Přidá soubor první průchodu výpis do seznamu.|  
|**/Sl**`width`|Nastaví šířku čáry zdroje výpis v znaků na řádek. Rozsah je 60 až 255 nebo 0. Výchozí hodnota je 0. Stejné jako [stránky](../../assembler/masm/page.md) šířku.|  
|**/Sn**|Při vytváření v seznamu vypne tabulky symbolů.|  
|**/SP**`length`|Nastaví délku stránky zdroje výpis řádků na stránce. Rozsah je 10 až 255 nebo 0. Výchozí hodnota je 0. Stejné jako [stránky](../../assembler/masm/page.md) délka.|  
|**/SS**`text`|Určuje text pro výpis zdroje. Stejné jako [SUBTITLE](../../assembler/masm/subtitle.md) text.|  
|**/St**`text`|Určuje název zdrojového seznamu. Stejné jako [název](../../assembler/masm/title.md) text.|  
|**/SX**|Zapne false podmíněné příkazy v seznamu.|  
|**/Ta**`filename`|Sestaví zdrojový soubor, jehož název nekončí příponou .asm.|  
|**/w**|Stejné jako **/W0/WX**.|  
|**/W**`level`|Nastaví úroveň pro upozornění, kde `level` = 0, 1, 2 nebo 3.|  
|**/WX**|Vrátí kód chyby, pokud se upozornění.|  
|**/X**|Ignorujte cesta zahrnutí prostředí.|  
|**/Zd**|Generuje číslo řádku informace do souboru objektu.|  
|**/ZF**|Díky všechny symboly veřejné.|  
|**/Zi**|Generuje CodeView informace do souboru objektu.|  
|**/Zm**|Umožňuje**M510** možnost pro maximální kompatibility s MASM 5.1.<br /><br /> Není k dispozici v ml64.exe.|  
|**/Zp**[[`alignment`]]|Struktury balíčky v zadané bajtové hranic. `alignment` Může být 1, 2 nebo 4.|  
|**/ZS**|Provede pouze kontrola syntaxe.|  
|**/?**|Zobrazí souhrn ML syntaxe příkazového řádku.|  
  
 `filename`  
 Název souboru.  
  
 `linkoptions`  
 Možnosti odkazů.  V tématu [možnosti Linkeru](../../build/reference/linker-options.md) Další informace.  
  
## <a name="remarks"></a>Poznámky  
 Některé možnosti příkazového řádku k použití nástroje ML a ml64 v příkazovém jsou závislé na umístění. Například protože ML a ml64 v příkazovém může přijmout několik **/c** možnosti, všechny odpovídající **/Fo** musí být zadané možnosti před **/c**. Příkazového řádku následující příklad znázorňuje specifikaci souboru objekt pro každou specifikaci souboru sestavení:  
  
 **ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**  
  
## <a name="environment-variables"></a>Proměnné prostředí  
  
|Proměnná|Popis|  
|--------------|-----------------|  
|INCLUDE|Určuje cestu pro zahrnout soubory hledání.|  
|ML|Určuje výchozí možnosti příkazového řádku.|  
|TMP|Určuje cestu pro dočasné soubory.|  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)   
 [Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)