---
title: Postup ohlášení problému se sadou nástrojů pro Visual C++
ms.date: 06/21/2018
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 7758905f6db537260ec9e8b6e516bfa409e97ad2
ms.sourcegitcommit: fbc05d8581913bca6eff664e5ecfcda8e471b8b1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2019
ms.locfileid: "56809734"
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset-or-documentation"></a>Postup ohlášení problému se sadou nástrojů Visual C++ nebo dokumentace

Pokud narazíte na potíže s kompilátorem Microsoft Visual C++, linkeru, nebo jiné nástroje a knihovny, chceme informovat o. Pokud se problém nachází v naší dokumentaci, chcete vědět, že příliš.

## <a name="how-to-report-a-c-toolset-issue"></a>Postup ohlášení problému sadu nástrojů s C++

Nejlepší způsob, jak nám dejte vědět o problému se nám pošlete zprávu, která obsahuje popis problému, kterým jste se setkali, podrobnosti o jak už vytváříte aplikace a *reprodukci*, můžeme použít pro reprodukci dokončení testovacího případu problém na našich počítačích. Tyto informace umožňují rychle ověřte, že problém v kódu existuje a není místní pro vaše prostředí k určení, jestli to má vliv na jiných verzí kompilátoru a Diagnostikujte příčinu.

V následujících částech nemusíte se věnovat čtení o kvůli tomu užitečnou sestavu, jak vygenerovat reprodukci pro typ problému, který jste našli a jak odesílat sestavy týmu. Sestavy jsou důležité pro nás a s ostatními vývojáři, jako jste vy. Děkujeme vám za pomoc při vylepšení Visual C++.

## <a name="how-to-prepare-your-report"></a>Jak připravit vaše sestava

Vytváření vysoce kvalitních sestavy je důležité, protože je velmi obtížné reprodukovat problém, který jste narazili na na našich počítačích bez úplné informace. Tím lepší vaše sestava je, tím více efektivně jsme se mohli znovu vytvořit a Diagnostikujte problém.

Minimálně musí obsahovat vaše sestavy

- Informace o úplnou verzi sady nástrojů, které používáte.

- Úplné cl.exe příkazovým řádkem použitým k sestavení vašeho kódu.

- Podrobný popis, které jste narazili na problém.

- Reprodukci: Příklad kompletní, zjednodušená a samostatná zdrojového kódu, který demonstruje daný problém.

Přečtěte si další informace o konkrétní informace potřebujeme a místo, kde najdete a jak vytvořit dobré reprodukci.

### <a name="the-toolset-version"></a>Verzi sady nástrojů

Budeme potřebovat informace o úplnou verzi a Cílová architektura sady nástrojů, které způsobí, že problém, jsme mohli otestovat vaši reprodukovat na stejnou sadu nástrojů na našich počítačích. Pokud jsme dokážete problém reprodukovat, tyto informace nám také poskytuje výchozí bod k prozkoumání dalších verzích nástrojů vykazuje stejný problém.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>Do sestavy plnou verzi kompilátoru, které používáte

1. Otevřít **Developer Command Prompt** , která odpovídá verzi a konfigurace architektury sady Visual Studio používá k sestavení projektu. Například, pokud vytvoříte pomocí sady Visual Studio 2017 na x64 x64 cíle, zvolte **x64 Native Tools Command Prompt pro VS 2017**. Další informace najdete v tématu [zkratky příkazového řádku pro vývojáře](build/building-on-the-command-line.md#developer-command-prompt-shortcuts).

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl /Bv**.

Výstup by měl vypadat nějak takto:

```Output
C:\Users\username\Source>cl /Bv
Microsoft (R) C/C++ Optimizing Compiler Version 19.14.26428.1 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\cl.exe:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1xx.dll:      Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c2.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\link.exe:      Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\mspdb140.dll:  Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\1033\clui.dll: Version 19.14.26428.1

cl : Command line error D8003 : missing source filename
```

Zkopírujte a vložte celý výstup do sestavy.

### <a name="the-command-line"></a>Příkazový řádek

Potřebujeme přesné příkazového řádku (cl.exe a všechny její argumenty) použít k sestavení vašeho kódu tak, že jsme ho vytvořili stejným způsobem na našich počítačích. To je důležité, protože problém, který jste se setkali může existovat pouze při sestavování s konkrétní argument nebo kombinace argumentů.

Nejlepší místo, kde najdete tyto informace je do protokolu sestavení ihned po dochází k problému. Tím se zajistí, že příkazový řádek obsahuje přesně stejné argumenty, které mohou způsobovat potíže.

#### <a name="to-report-the-contents-of-the-command-line"></a>K hlášení obsah příkazového řádku

1. Vyhledejte **CL.command.1.tlog** souboru a otevřete ho. Ve výchozím nastavení, je tento soubor umístěn ve složce Dokumenty v \\sady Visual Studio *verze*\\projekty\\*SolutionName* \\ *ProjectName*\\*konfigurace*\\*ProjectName*.tlog\\CL.command.1.tlog, nebo ve složce uživatele v části \\Zdroj\\úložišť\\*SolutionName*\\*ProjectName*\\*konfigurace* \\ *ProjectName*.tlog\\CL.command.1.tlog. Pokud používáte jiný sestavovací systém, nebo pokud jste změnili výchozí umístění pro váš projekt může být v jiném umístění.

   V tomto souboru najdete názvy souborů zdrojového kódu, za nímž následuje argumenty příkazového řádku umožňuje zkompilovat, každou na samostatných řádcích.

1. Vyhledejte řádek, který obsahuje název souboru zdrojového kódu, kde k problému dochází; řádek pod ním obsahuje odpovídající argumenty příkazu cl.exe.

Zkopírujte a vložte do sestavy celý příkazový řádek.

### <a name="a-description-of-the-problem"></a>Popis problému

Potřebujeme podrobný popis problému, který jste se setkali tak, aby bylo možné ověřit, že vidíme stejný účinek na našich počítačích; jeho také někdy užitečné nám vědět, co se snažíte dosáhnout a co jste očekávali.

Zadejte prosím **přesná chybové zprávy** dána na sadu nástrojů nebo chování přesné runtime se zobrazí. Potřebujeme tyto informace k ověření, že jsme jste správně reprodukovat problém. Uveďte **všechny** kompilátoru výstup, ne jenom poslední chybová zpráva. Potřebujeme na veškerý obsah, které vedly k problému, který budete sestavy. Pokud tento problém můžete duplikovat pomocí kompilátoru příkazového řádku, preferuje; se tento výstup kompilátoru integrované vývojové prostředí a jiných systémů buildů filtrovat chybové zprávy naleznete v tématu nebo zachytit pouze první řádek chybovou zprávu.

Pokud tento problém je, že kompilátor přijme neplatný kód a negeneruje diagnostiku, mějte prosím na paměti Toto v sestavě.

Pokud chcete nahlásit problém chování modulu runtime, zahrňte **přesná kopie** program vytiskne navýšení kapacity a co byste měli vidět. V ideálním případě by toto je vložený ve výstupu příkazu, například `printf("This should be 5: %d\n", actual_result);`. Pokud dojde k chybě programu, nebo přestane reagovat, zmiňovat, který také.

Přidáte další podrobnosti, které by nám mohly pomoct diagnostikovat problém, který zaznamenal/zaznamenala jste, jako je například všechny pracovní postupy, možná jste nalezené. Vyhněte se opakující se informace jinde v sestavě.

### <a name="the-repro"></a>Reprodukci

Reprodukci je příklad kompletní a samostatné zdrojového kódu, který reprodukovatelná demonstruje daný problém jste narazili (tedy název). Potřebujeme zkopírujte tak, že jsme chybu reprodukovat na našich počítačích. Kód by měl být dostatečně samostatně k vytvoření jednoduché spustitelný soubor, který zkompiluje a spustí nebo, který by zkompilovat a spustit, když pro problém, který jste našli. Reprodukci není fragment kódu; měl by mít kompletní funkce a třídy a obsahují všechny nezbytné #include i pro standardní záhlaví.

#### <a name="what-makes-a-good-repro"></a>Díky tomu dobrý reprodukci

Je dobré reprodukci:

- **Minimální.** Reprodukce by měl být co nejmenší ještě stále demonstrují, přesně, které jste narazili na problém. Reprodukce nemusí být komplexní nebo realistické; potřebují jenom zobrazit kód, který odpovídá standardní nebo implementace zdokumentovaných kompilátoru, nebo v případě chybějící diagnostické, kód, který není vyhovující. Jednoduché, na bod reprodukce, které obsahují pouze dostatek kód pro demonstraci problém jsou nejvhodnější. Pokud můžete eliminovat nebo zjednodušit kód a nadále splňovala podmínky shody a ponechat beze změny problém, proveďte to. Nemusíte zahrnovat čítače příklady kódu, který funguje.

- **Samostatná.** Reprodukce byste se vyhnout zbytečným závislosti. Pokud dokážete problém bez knihovny třetích stran reprodukovat, proveďte to. Pokud dokážete problém bez jakéhokoli kódu knihovny kromě jednoduché výstup příkazů reprodukovat (například `puts("this shouldn't compile");`, `std::cout << value;`, a `printf("%d\n", value);` jsou v pořádku), udělejte to prosím. To je ideální, pokud v příkladu můžete vyjádřit na jeden zdrojový soubor kódu, bez ohledu na záhlaví uživatele. Snižuje množství kódu, který máme považovat za možné přispěvatele, jak tento problém je enormously užitečné USA.

- **S nejnovější verzí kompilátoru.** Reprodukce používejte nejnovější aktualizace na nejnovější verzi sady nástrojů nebo nejnovější Předběžná verze další aktualizaci nebo další hlavní verze, kdykoli je to možné. Velmi často jsme opravili problémy, na které můžete narazit ve starších verzích sady nástrojů v novější verzi. Opravy jsou přeneseny zpět ke starším verzím pouze ve výjimečných případech.

- **Porovnávána s jinými kompilátory** podle potřeby. Reprodukce, které se týkají přenositelný kód C++ ověřte chování před jinými kompilátory, pokud je to možné. Standardní Určuje program správnosti a žádný kompilátor je ideálním řešením, ale při Clang a GCC přijmout kódu bez diagnostiku a MSVC tak není, bude pravděpodobně že se díváte na chybu v našich kompilátoru. (Další možnosti zahrnují rozdíly v chování systému Unix a Windows nebo různé úrovně implementaci standardů C++ atd.) Na druhé straně Pokud všechny kompilátory odmítnout kódu, pak je pravděpodobné, že váš kód je nesprávný. Zobrazuje různé chybové zprávy vám mohou pomoci diagnostikovat problém.

   Můžete najít seznam online kompilátory k testování kódu proti v [kompilátory Online C++](https://isocpp.org/blog/2013/01/online-c-compilers) na webu ISO C++ nebo to připravili [seznamu z Online kompilátory C++](https://arnemertz.github.io/online-compilers/) na Githubu. Některé konkrétní příklady [Wandbox](https://wandbox.org/), [kompilátoru Explorer](https://godbolt.org/), a [Coliru](http://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Websites online kompilátoru nejsou spojit s Microsoftem. Počet webů online kompilátoru jsou spouštěny jako osobní projekty a některé z těchto webů nemusí být k dispozici, když jste najdete v tomto, ale vyhledávání by měl najít jiné, která vám pomůže.

Problémy v kompilátoru, linkeru a v knihovnách, mají tendenci zobrazíte samotné zejména způsoby. Typ problému, se kterými určí, jaký druh reprodukci, měli byste zahrnout do sestavy. Bez odpovídající reprodukci nemáme nic o prověření. Tady jsou některé druhy problémů, které se mohou objevit a pokyny pro generování druhy reprodukce, že používejte k hlášení jednotlivé typy problémů.

#### <a name="frontend-parser-crash"></a>Při selhání front-endu (Analyzátor)

Ve fázi analýzy kompilátoru dochází ke zhroucení front-endu. Obvykle bude kompilátor generovat [závažná chyba C1001](error-messages/compiler-errors-1/fatal-error-c1001.md) a odkazují zdrojový kód souboru a číslo řádku na kterém došlo k chybě; to se často zmiňovat msc1.cpp souboru, ale můžete ignorovat těchto podrobných informací.

Pro tento typ selhání, zadejte [Předzpracovaná reprodukci](#preprocessed-repros).

Tady je příklad výstupu kompilátoru pro tento typ selhání:

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend-code-generation-crash"></a>Selhání back-endu (generování kódu)

Při fázi generování kompilátoru kódu dochází ke zhroucení back-endu. Obvykle bude kompilátor generovat [závažná chyba C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)a často je budou upozorňovat kompilátoru soubor nemusí odkazovat na soubor zdrojového kódu a související s problémem, který číslo řádku;\\utc\\src\\p2\\main.c, ale můžete ignorovat těchto podrobných informací.

Pro tento typ selhání, zadejte [spojení reprodukce](#link-repros) používáte kódu generování při propojování (LTCG) zajišťuje **/GL** argument příkazového řádku do cl.exe. Pokud ne, zadejte [Předzpracovaná reprodukci](#preprocessed-repros) místo.

Tady je příklad výstupu kompilátoru selhání back-endu, ve kterém se nepoužívá LTCG. Pokud to vypadá výstup kompilátoru by měla poskytnout [Předzpracovaná reprodukci](#preprocessed-repros).

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

Pokud řádek, který začíná **vnitřní chyba KOMPILÁTORU** uvádí link.exe, spíše než cl.exe, LTCG byl povolen a měli byste zadat [spojení reprodukce](#link-repros). Pokud není jasné, jestli má LTCG byl z chybových zpráv kompilátoru, budete muset Zkontrolujte argumenty příkazového řádku, které jste zkopírovali ze sestavení protokolu v předchozím kroku pro **/GL** argument příkazového řádku.

#### <a name="linker-crash"></a>Selhání linkeru

Během fáze propojení, po spuštění kompilátoru dojde k selhání propojovacího programu. Obvykle bude generovat linker [chyba Linkerů LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Pokud výstup uvádí C1001 nebo zahrnuje generování kódu při propojování odkaz, podívejte se na [back-endu (generování kódu) selhání](#backend-code-generation-crash) místo pro další informace.

Pro tento typ selhání, zadejte [spojení reprodukce](#link-repros).

Tady je příklad výstupu kompilátoru pro tento typ selhání.

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

Pokud je povoleno přírůstkové propojení a až po úspěšném počáteční odkaz, došlo k selhání (tedy až po první úplné propojení na kterých je založena následné přírůstkové propojení) zadejte také kopii objekt (.obj) a soubory knihoven (.lib), který odpovídají zdrojové soubory, které byly změněny po dokončení počáteční odkaz.

#### <a name="bad-code-generation"></a>Generování chybného kódu

Generování chybného kódu není obvyklé, ale nastane, pokud kompilátor omylem generuje nesprávný kód, který způsobí, že vaše aplikace k chybě v modulu runtime spíše než zjišťování tento problém v době kompilace. Pokud si myslíte, že problém výsledky dochází v generování chybného kódu, považovat za sestavy stejné [back-endu (generování kódu) selhání](#backend-code-generation-crash).

Pro tento typ selhání zadejte [spojení reprodukce](#link-repros) používáte kódu generování při propojování (LTCG) zajišťuje **/GL** argument příkazového řádku do cl.exe. Zadejte prosím [Předzpracovaná reprodukci](#preprocessed-repros) Pokud tomu tak není.

## <a name="how-to-generate-a-repro"></a>Postup generování reprodukci

Nás sledovat příčiny problému, abychom [dobré reprodukci](#what-makes-a-good-repro) je důležité. Než uděláte některý z kroků uvedených níže pro konkrétní druhy reprodukce, zkuste zmenšit kód, který ukazuje, co nejvíce problémů. Zkuste vyloučit nebo minimalizovat závislosti, požadované hlavičky a knihovny a omezit možnosti kompilátoru a definice preprocesoru, pokud je to možné použít.

Níže jsou uvedeny pokyny pro generování různé druhy reprodukce, který použijete k sestavě různé druhy problémů.

### <a name="preprocessed-repros"></a>Předzpracovaná reprodukce

A *předzpracovaná reprodukci* je jeden zdrojový soubor, který ukazuje problém, generuje z výstupu preprocesoru jazyka C pomocí **/P** – možnost kompilátoru na původní zdrojový soubor reprodukovat. Tento inlines zahrnutých hlaviček odebrání závislostí na další zdroje a soubory hlaviček a také řeší makra, #ifdefs a dalších příkazů preprocesoru, které by mohly závisí vaše místní prostředí.

> [!NOTE]
> Předzpracovaná reprodukce tak užitečné nejsou pro problémy, které mohou být způsobeny chyby v naší implementaci standardní knihovny, protože jsme se často mají být nahrazeny naše nejnovější, v průběhu provádění chcete zobrazit, zda již Opravili jsme problém. V takovém případě není předzpracování reprodukci a v případě nemůžete zmenšit balíček kódu do souboru .zip nebo podobné problém, který chcete jeden zdrojový soubor, nebo zvažte použití reprodukci projektu integrovaného vývojového prostředí. Další informace najdete v tématu [další reprodukce](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Chcete-li předběžné zpracování souboru zdrojového kódu

1. Argumenty příkazového řádku použít k sestavení reprodukci, jak je popsáno v zachycení [hlášení obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřít **Developer Command Prompt** , která odpovídá verzi a konfigurace architektury sady Visual Studio používá k sestavení projektu.

1. Přejděte do adresáře, který obsahuje projekt reprodukovat.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl /P** *argumenty* *filename.cpp*, kde *argumenty* je Seznam argumentů, které jsou zachyceny výše, a *filename.cpp* je název zdrojového souboru reprodukovat. Tento příkaz replikuje příkazovým řádkem použitým pro reprodukci, ale přeruší kompilaci po průchodu preprocesoru a vypíše předzpracovaná zdrojový kód a *filename*. jsem.

Pokud jsou předzpracování jazyka C + +/ CX souboru se zdrojovým kódem, nebo použití funkce moduly C++, jsou nutné některé další kroky. Další informace najdete v níže uvedených částech.

Po vygenerování předzpracovaného souboru, je vhodné Ujistěte se, že stále reprodukce problémů pomocí předzpracovaného souboru.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Potvrďte, že je chyba stále reprodukce s Předzpracovaný soubor

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl** *argumenty* **/TP** *filename*.i říct cl.exe ke kompilaci předzpracovaného souboru jako zdrojový soubor jazyka C++, kde *argumenty* je seznam argumentů, které jsou zachyceny výše, ale s žádným **/D** a **/I** argumenty odstranit, (protože jsou již byly zahrnuty v souboru předzpracovaná); a pokud *filename*.i je název předzpracovaného souboru.

1. Potvrďte, že je problém reprodukovat.

Nakonec připojit předzpracovaná reprodukci *filename*.i do sestavy.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Předzpracovaná C + +/ CX WinRT/UPW reprodukce kódu

Pokud používáte C + +/ CX sestavit spustitelný soubor, existují některé další kroky potřebné k vytvoření a ověření předzpracovaná reprodukovat.

#### <a name="to-preprocess-ccx-source-code"></a>Chcete-li předzpracování jazyka C + +/ CX zdrojového kódu

1. Vytvoření předzpracovaného zdrojového souboru, jak je popsáno v [se předběžně zpracovat soubor zdrojového kódu](#to-preprocess-a-source-code-file).

1. Hledat generované _filename_.i souboru **#using** direktivy.

1. Zkontrolujte seznam všech odkazovaných souborů. Vynechat všechny Windows\*soubory .winmd, platform.winmd soubory a knihovny mscorlib.dll.

Abyste mohli ověřit, že Předzpracovaný soubor stále reprodukuje problém

1. Vytvořte nový adresář pro Předzpracovaný soubor a zkopírujte ho do nového adresáře.

1. Zkopírujte soubory .winmd z vaší **#using** seznamu do nového adresáře.

1. V novém adresáři vytvořte soubor prázdný vccorlib.h.

1. Upravte Předzpracovaný soubor odstraňte přitom všechny **#using** direktivy pro knihovnu mscorlib.dll.

1. Upravte soubor předzpracovaná změnit libovolné absolutní cesty na jenom úplné názvy souborů pro soubory zkopírovaný .winmd.

Potvrďte, že Předzpracovaný soubor stále reprodukuje problém, jak je uvedeno výše.

### <a name="preprocessed-c-modules-repros"></a>Předzpracovaná reprodukce moduly C++

Pokud používáte moduly funkce kompilátoru jazyka C++, existují některé jiné kroky potřebné k vytvoření a ověření předzpracovaná reprodukovat.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Předběžné zpracování souboru zdrojového kódu, který používá modul

1. Argumenty příkazového řádku použít k sestavení reprodukci, jak je popsáno v zachycení [hlášení obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřít **Developer Command Prompt** , která odpovídá verzi a konfigurace architektury sady Visual Studio používá k sestavení projektu.

1. Přejděte do adresáře, který obsahuje projekt reprodukovat.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl /P** *argumenty* *filename.cpp*, kde *argumenty* je Seznam argumentů, které jsou zachyceny výše, a *filename.cpp* je název zdrojového souboru, která využívá modul.

1. Přejděte do adresáře, který obsahuje reprodukci projekt, který je sestaven rozhraní modulu (.ifc výstup).

1. Zachycení argumenty příkazového řádku použít k sestavení rozhraní modulu.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl /P** *argumenty* *modulename.ixx*, kde *argumenty* je Seznam argumentů, které jsou zachyceny výše, a *modulename.ixx* je název souboru, který vytvoří rozhraní modulu.

Po vygenerování předzpracovaných souborů, je vhodné zajistit stále reprodukce problémů pomocí předzpracovaného souboru.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Potvrďte, že je chyba stále reprodukce s Předzpracovaný soubor

1. V okně konzoly pro vývojáře změňte zpět do adresáře, který obsahuje projekt reprodukovat.

1. Zadejte příkaz **cl** *argumenty* **/TP** *filename*.i jak je uvedeno výše, chcete-li zkompilovat předzpracovaného souboru, jako by šlo zdrojový soubor jazyka C++.

1. Potvrďte, že problém bude reprodukován stále Předzpracovaný soubor.

Nakonec připojit soubory předzpracovaná reprodukci (*filename*.i a *modulename*.i) společně s výstupem .ifc do sestavy.

### <a name="link-repros"></a>Spojení reprodukce

A *propojit reprodukci* je obsah adresáře určeného vytvořeného v propojovacím programu **odkaz\_reprodukci** proměnné prostředí. Obsahuje artefaktů sestavení, které společně ukazují problém, ke které dochází v době spojení, jako je například selhání back-endu zahrnující kódu generování při propojování (LTCG) nebo selhání propojovacího programu. Tyto artefakty sestavení jsou ty, které jsou potřeba jako linkeru vstupní, tak, aby problém možné reprodukovat. Spojení reprodukce můžete snadno vytvořit pomocí této proměnné prostředí povolit funkci generování integrované reprodukci linkeru.

#### <a name="to-generate-a-link-repro"></a>Ke generování odkazu reprodukci

1. Argumenty příkazového řádku použít k sestavení reprodukci, jak je popsáno v zachycení [hlášení obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřít **Developer Command Prompt** , která odpovídá verzi a konfigurace architektury sady Visual Studio používá k sestavení projektu.

1. V okně konzoly příkazového řádku pro vývojáře přejděte do adresáře, který obsahuje projekt reprodukovat.

1. Zadejte **mkdir linkrepro** vytvořit adresář pro reprodukci odkaz.

1. Zadejte příkaz **nastavit odkaz\_reprodukci = linkrepro** nastavit **odkaz\_reprodukci** proměnnou prostředí k adresáři, který jste právě vytvořili. Pokud vaše sestavení běží z jiného adresáře, jak se často stává třeba u složitějších projektů, nastavte **odkaz\_reprodukci** úplnou cestu k adresáři linkrepro místo.

1. Sestavit projekt reprodukovat v sadě Visual Studio, v okně konzoly příkazového řádku pro vývojáře zadejte příkaz **devenv**. To zajistí, že hodnota **odkaz\_reprodukci** proměnnou prostředí je viditelná pro Visual Studio. K vytvoření projektu na příkazovém řádku použijte argumenty příkazového řádku zachycené nad duplikovat reprodukci sestavení.

1. Sestavení projektu reprodukci a potvrďte, že očekávané problému došlo.

1. Pokud jste použili k provedení sestavení, zavřete sadu Visual Studio.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **nastavit odkaz\_reprodukci =** zrušte **odkaz\_reprodukci** proměnné prostředí.

Nakonec balíček reprodukci kompresí celý linkrepro adresáře do souboru .zip nebo podobné a připojte ji do sestavy.

### <a name="other-repros"></a>Další reprodukce

Pokud tento problém nemůžete zmenšit jeden zdrojový soubor nebo předzpracovaná reprodukci a problém nevyžaduje spojení reprodukce, prozkoumáme projekt integrované vývojové prostředí. Všechny pokyny o tom, jak vytvořit dobré reprodukci stále platí; Kód by měl být minimální a samostatná, problém se budou objevovat v naší nejnovější nástroje, a pokud je to potřeba, problém by neměl vidět v jiné kompilátory.

Vytvoření vašeho reprodukci jako minimální projekt integrované vývojové prostředí, pak balíček kompresí celý adresářovou strukturu do souboru .zip nebo podobné a připojte ji do sestavy.

## <a name="ways-to-send-your-report"></a>Způsoby, jak odeslat sestavy

Existuje několik dobré způsobů, jak získat sestavy na nás. Můžete použít předdefinované sady Visual Studio [nástrojem ohlásit problém](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017), nebo [komunity vývojářů v aplikaci Visual Studio](https://developercommunity.visualstudio.com/) stránky. Získáte taky přímo na našich stránkách komunity vývojářů výběrem **názor na produkt** tlačítko v dolní části této stránky. Výběr závisí na, jestli chcete použít nástrojů integrovaných v prostředí IDE pro zachytávání snímků obrazovky a uspořádání sestavy pro příspěvky na stránkách komunity vývojářů, nebo pokud si přejete použít přímo na webu.

> [!NOTE]
> Bez ohledu na to, jak odeslat sestavu Microsoft respektuje vaše soukromí. Microsoft usiluje o dodržování předpisů se všemi zákony na ochranu dat a nařízení. Informace o tom, jak jsme zpracovávat data, která nám pošlete, najdete v článku [prohlášení o ochraně osobních údajů Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="use-the-report-a-problem-tool"></a>Pomocí sestavy nástroje problému

**Nahlásit problém** nástroje v sadě Visual Studio je způsob, jak uživatelům aplikace Visual Studio nahlásit celou řadu problémů pomocí několika kliknutí. Poskytuje jednoduchý formulář, který můžete zadat podrobné informace o tomto problému jste se setkali a pak odeslat sestavu bez opuštění integrovaného vývojového prostředí.

Generování sestav prostřednictvím vašeho problému **nahlásit problém** nástroj je snadný a pohodlný z integrovaného vývojového prostředí. Můžete k němu přístup ze záhlaví výběrem **odeslat zpětnou vazbu** ikonu vedle **Snadné spuštění** vyhledávacího pole, nebo můžete najít na panelu nabídek v **pomáhají**  >  **Poslat svůj názor** > **nahlásit problém**.

Pokud budete chtít nahlásit problém, nejprve hledat komunity vývojářů s podobnými problémy. Pokud váš problém byl ohlášen dřív, a podpořit svým hlasem tématu a přidání komentářů se další podrobnosti. Pokud nevidíte podobný problém, zvolte **ohlásit nový problém** tlačítko v dolní části dialogového okna zpětná vazba na Visual Studio a postupujte podle kroků zprávu o problému.

### <a name="use-the-visual-studio-developer-community-pages"></a>Použít na stránkách komunity vývojářů v aplikaci Visual Studio

Na stránkách komunity vývojářů v aplikaci Visual Studio jsou jiné pohodlný způsob, jak zprávy o problémech a najděte řešení pro Visual Studio a jazyka C++ kompilátor, nástroje a knihovny. Existují určité komunity vývojářů stránky pro [sady Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html), [Visual Studio for Mac](https://developercommunity.visualstudio.com/spaces/41/index.html), [.NET](https://developercommunity.visualstudio.com/spaces/61/index.html), [C++](https://developercommunity.visualstudio.com/spaces/62/index.html), [ Azure DevOps](https://developercommunity.visualstudio.com/spaces/21/index.html), a [TFS](https://developercommunity.visualstudio.com/spaces/22/index.html). Pod tyto karty v horní části každé stránky je vyhledávací pole, která vám pomůže najít příspěvky nebo témata, která zprávy o problémech, které jsou podobné. Možná zjistíte, že řešení a další užitečné informace týkající se vašeho problému je již k dispozici. Pokud někdo ohlásil stejný problém před, podpořit svým hlasem a komentářů k tomuto tématu ne vytvořit nové hlášení o problému. Komentovat, hlasovat nebo nahlásit nový problém, můžete být vyzváni k přihlášení k účtu Visual Studio a vyjádření souhlasu komunity vývojářů v aplikaci dáte přístup k vašemu profilu.

Pro problémy s použitím C++ kompilátoru, linkeru a další nástroje a knihovny, [C++](https://developercommunity.visualstudio.com/spaces/62/index.html) stránky. Pokud hledáte váš problém a nebyla hlášena před, zvolte **nahlásit problém** tlačítko vedle pole Hledat v horní části stránky. Může obsahovat kód reprodukci a příkazového řádku, snímky obrazovky, odkazy na související diskuse a další informace, které si myslíte, že je důležité a užitečné.

> [!TIP]
> Pro jiné druhy problémů může dojít v sadě Visual Studio, které nesouvisí s sadu nástrojů pro C++ (například problémy uživatelského rozhraní, fungovat funkce integrovaného vývojového prostředí nebo obecné selhání), použijte **nahlásit problém** nástroje v integrovaném vývojovém prostředí. Toto je nejlepší volbou z důvodu možnosti snímku obrazovky a jeho funkcí záznamu akce uživatelského rozhraní, které vedly k problém, který jste se setkali. Tyto druhy chyb lze také vyhledávat [komunity vývojářů](https://developercommunity.visualstudio.com/) lokality. Další informace najdete v tématu [postup ohlášení problému se sadou Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

### <a name="reports-and-privacy"></a>Sestavy a ochrana osobních údajů

Ve výchozím nastavení **všechny informace v sestavách a všechny komentáře a odpovědi jsou veřejně viditelné**. Za normálních okolností jde výhody, protože umožňuje celé komunitě zobrazíte problémů, řešení a řešení, které našli ostatním uživatelům. Pokud máte obavy o tom, že vaše data nebo identity veřejného z důvodů duševní vlastnictví nebo osobních údajů, ale máte možnosti.

Pokud máte obavy o odhalení svoji identitu [vytvořit nový účet Microsoft](https://signup.live.com/) , který nesmí vyzradit žádné podrobnosti o vás. Vytvoření sestavy pomocí tohoto účtu.

**Neumisťujte všechno, co chcete zachovat privátní v nadpisu nebo obsahu objektu původní sestavy, což je veřejná.** Místo toho Všimněte si, že chcete odeslat podrobnosti soukromě v samostatných komentář. Pokud chcete mít jistotu, že se vaše sestava směřuje těm správným lidem, zahrňte **cppcompiler** v seznamu témat hlášení o problému. Po vytvoření hlášení o problému, je teď možné určit, kdo uvidí vaše odpovědi a přílohy.

#### <a name="to-create-a-problem-report-for-private-information"></a>Vytvoření hlášení o problému pro soukromé informace

1. V sestavě můžete vytvořit zvolte **přidat komentář** k vytvoření soukromého popisu problému.

1. V editoru odpovědi pomocí ovládacího prvku rozevíracího seznamu níže **odeslat** a **zrušit** tlačítka zadejte cílovou skupinu pro odpovědi. Pouze lidé, se kterými můžete zadat můžete zobrazit tyto soukromé odpovědi a všechny Image, odkazy nebo kódu, které jsou v nich. Zvolte **Viewable moderátoři a původní plakát** omezit viditelnost zaměstnancům společnosti Microsoft a sami.

1. Přidáte popis a jakékoli jiné informace, obrázky a přiložené soubory potřebné pro vaše reprodukci. Zvolte **odeslat** tlačítko soukromě odesílat tyto informace.

   Všimněte si, že je 2GB limit připojených souborů a maximálně 10 soubory. Žádné větší nahrávání požádejte o adresu URL odeslání do privátní komentáře.

Veškeré odpovědi pod tento komentář mají stejnou viditelnost s omezeným přístupem, které jste zadali. To platí i v případě, že ovládací prvek rozevírací seznam v odpovědi není uveden stav zobrazení s omezeným přístupem správně.

Chcete-li udržovat vaše osobní údaje a udržovat vaše citlivé informace z veřejné zobrazení, Postarejte se prosím k odpovědím v rámci této omezené komentář zachovat všechny interakce s Microsoftem. Odpovědi na další komentáře může vést k neúmyslně zveřejnit citlivé informace.

## <a name="how-to-report-a-c-documentation-issue"></a>Postup ohlášení problému dokumentaci jazyka C++

Problémy s úložištěm GitHub používáme ke sledování problémů, které jsou uvedeny v naší dokumentaci. Nyní můžete vytvořit Githubu problémy přímo ze stránky obsahu, který vám umožní pracovat způsobem mnohem bohatší zapisovače a produktových týmů. Pokud narazíte na problém s dokumentem, ukázka chybného kódu, matoucí vysvětlení, kritické vynechání nebo jenom překlep, které lze snadno dejte nám vědět. Přejděte do dolní části stránky a vyberte **přihlásit se a poskytnout názor na dokumentaci**. Budete muset vytvořit účet Githubu, pokud již nemáte, ale až to uděláte, můžete zobrazit všechny problémy v naší dokumentaci, jejich stav a odeslání oznámení, když dojde ke změně pro problém, který jste nahlásili. Další informace najdete v tématu [A novou zpětnou vazbu systém přichází na web docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Při vytváření dokumentace problém na Githubu pomocí tlačítka dokumentace ke službě, problém se automaticky vyplní některé informace o stránku, kterou jste vytvořili problému, abychom věděli, kde se nachází problém. Neupravujte prosím tyto informace. Stačí připojte podrobnosti o tom, co je špatně a pokud chcete, navrhované opravy. [Naše dokumentace je open source](https://github.com/MicrosoftDocs/cpp-docs/), takže pokud chcete skutečně proveďte opravu a navrhovat sami, můžete to udělat. Další informace o jak přispívat k naší dokumentaci najdete v tématu naše [využité průvodce](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) na Githubu.

