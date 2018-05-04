---
title: Spuštění knihovny LIB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c306ba58bfef11f92d7e861272aad2aa605c8fde
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="running-lib"></a>Spuštění knihovny LIB
Různé možnosti příkazového řádku můžete použít k řízení LIB.  
  
## <a name="lib-command-line"></a>LIB příkazového řádku  
 Chcete-li spustit LIB, zadejte příkaz `lib` následovaný možností a názvy souborů pro úlohu používáte LIB k provedení. LIB také přijme příkazového řádku vstup v příkazu soubory, které jsou popsané v následující části. LIB nepoužívá proměnné prostředí.  
  
> [!NOTE]
>  Pokud jste zvyklí LINK32.exe a LIB32.exe nástroje poskytované s Microsoft Win32 Software Development Kit pro Windows NT, může používáte buď příkaz `link32 -lib` , nebo pomocí příkazu `lib32` Správa knihoven a vytvoření Importujte knihovny. Ujistěte se, chcete-li změnit vaše soubory pravidel a dávkové soubory použít `lib` místo příkazu.  
  
## <a name="lib-command-files"></a>Soubory příkazů LIB  
 Argumenty příkazového řádku můžete předat LIB v soubor příkazů pomocí následující syntaxe:  
  
```  
LIB @commandfile  
```  
  
 Soubor `commandfile` je textový soubor. Je povolen žádný místa nebo kartě mezi znaku zavináče (@) a název souboru. Neexistuje žádný výchozí rozšíření; je nutné zadat úplný název souboru, včetně všech rozšíření. Zástupné znaky nelze použít. Absolutní nebo relativní cesta můžete zadat název souboru.  
  
 V souboru příkaz argumenty může být odděleno mezerami nebo karty, jako je tomu v příkazovém řádku; také je možné oddělit znaky nového řádku. K označení komentář použijte středník (;). LIB ignoruje všechny text z středník na konec řádku.  
  
 Můžete zadat část nebo celý příkazového řádku v souboru příkazů a můžete použít více než jeden soubor příkazů v příkazu LIB. LIB přijme vstupní soubor příkazů, jako kdyby byly zadány v tomto umístění na příkazovém řádku. Soubory příkazů nelze vnořit. LIB vrátí obsah souborů příkaz, pokud se používá možnost/nologo.  
  
## <a name="using-lib-options"></a>Pomocí možností LIB  
 Možnost se skládá z specifikátor možnosti, která je pomlčkou (-) nebo lomítkem (/), za nímž následuje název možnosti. Názvy možností nelze zkracovat. Některé možnosti trvat argument, zadáno po dvojtečkou (:). Ve specifikaci možnosti nejsou povoleny mezery ani tabulátory. Jednotlivé specifikace možností lze na příkazovém řádku oddělit jednou nebo více mezerami či tabulátory. Názvy možností a jejich – klíčové slovo nebo soubor název argumenty nejsou velká a malá písmena, ale identifikátory používané jako argumenty se velká a malá písmena. LIB zpracovává možnosti v pořadí zadaném v příkazovém řádku a soubory příkazů. Pokud se možnost opakuje s jinou argumenty, byl naposledy mají být zpracovány přednost.  
  
 Následující možnosti použít na všechny režimy LIB:  
  
 / ERRORREPORT [NONE &AMP;#124; VÝZVA &AMP;#124; FRONTY &AMP;#124; ODESLAT]  
 Pokud se nezdaří lib.exe za běhu, můžete/errorreport odesílat informace společnosti Microsoft o tyto interní chyby.  
  
 Další informace o/errorreport najdete v tématu [/errorreport (sestava interními chybami kompilátoru)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 / LTCG  
 Způsobí, že knihovnu, která má být sestaven pomocí kódu v době propojování generace.  Další informace najdete v tématu [/ltgc](../../build/reference/ltcg-link-time-code-generation.md).  
  
 / MACHINE  
 Určuje cílovou platformu programu. Obvykle není potřeba zadat /MACHINE. LIB odvodí typ počítač ze soubory .obj. V některých případech ale LIB nelze určit typ počítače a vydá chybovou zprávu. Pokud k takové chybě dojde, zadejte volbu /MACHINE. V režimu/extract tato možnost je pouze k ověření. Použití `lib /?` na příkazovém řádku zobrazíte typů dostupných počítačů.  
  
 /NOLOGO  
 Potlačí zobrazení LIB autorským zprávu a verze číslo a zabraňuje zobrazování příkaz souborů.  
  
 / VERBOSE  
 Zobrazí podrobnosti o průběhu relace, včetně názvů soubory .obj, který chcete přidat. Informace se odesílají do standardního výstupního a můžete přesměrovat do souboru.  
  
 /WX [: NE]  
 Upozornění považovat za chyby. V tématu [wdn (považovat upozornění Linkeru jako chyby)](../../build/reference/wx-treat-linker-warnings-as-errors.md) Další informace.  
  
 Další možnosti platí pouze pro konkrétní režimy LIB. Tyto možnosti jsou popsané v části popisující oba režimy.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)