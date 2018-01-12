---
title: "Postup nahlásit problém s sady nástrojů Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 1/03/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1a5cdb873d536702ecf8536d9a9e7c0205cc923
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset"></a>Postup nahlásit problém s sady nástrojů Visual C++

Pokud narazíte na potíže s Visual C++ compiler, linkeru nebo jiných nástrojů, chceme vědět o nich.

Nejlepší způsob, jak dejte nám vědět o problému, je pošlete nám sestavu, která obsahuje popis problému, který byla zjištěna, podrobnosti o tom, jak sestavujete vašeho programu a určitý kód, který jsme slouží pro reprodukci problému na naší vlastní počítače. Tyto informace umožňují nám rychle ověřte, zda problém existuje a není místní prostředí, určují, jestli to nepříznivě ovlivňuje jiné verze kompilátoru a diagnostikovat jeho příčinu.

V tomto dokumentu budete přečíst si o

- [Postup přípravy sestavy](#prepare), a díky užitečnou sestavu.

- [Jak vygenerovat zkopírujte](#generate)a různé druhy repros.

- [Způsoby odeslání sestavy](#send), a jsou co pak jiný.

Sestavy jsou důležité pro nás a ostatní vývojáři mohou. Děkujeme vám za pomoc při vylepšení Visual C++.

## <a name="prepare"></a>Postup přípravy sestavy

Vytváření vysoce kvalitní sestavy je důležité, protože jeho velmi obtížné reprodukujte problém došlo na vlastní počítače bez úplné informace. Tím lepší je sestavy, čím efektivně jsme se může znovu vytvořte a diagnostikovat problém.

Minimálně musí obsahovat sestavy

- Úplné informací o verzi sady nástrojů, které používáte.

- Úplné cl.exe příkazovým řádkem použitým k vytvoření vašeho kódu.

- Podrobný popis problému, který jste se setkali.

- Zkopírujte: zdrojový kód, který ukazuje problém.

Přečtěte si další informace o konkrétní informace jsme potřeba a tam, kde můžete najít.

### <a name="the-toolset-version"></a>Sada nástrojů verze

Potřebujeme informace plnou verzi sady nástrojů, které používáte, jsme mohli otestovat vaši zkopírujte proti stejné sady nástrojů na našem počítače. Pokud jsme lze problém reprodukovat, tyto informace nám také poskytuje výchozí bod pro zkoumání jaké další verze sady nástrojů vykazuje stejný problém.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>K sestavě na plnou verzi, kterou používáte kompilátoru

1. Na klávesnici stiskněte klávesu Windows a začněte psát `Developer Command Prompt`.

1. Vyberte **příkazový řádek vývojáře** verze, která odpovídá verzi sady Visual Studio používáte když se objeví v seznamu odpovídá.

1. V **příkazový řádek vývojáře** konzole, zadejte příkaz `cl /Bv /CLR`.

Výstup by měl vypadat podobně jako tento:

```Output
C:\Compiler>cl /Bv /CLR
Microsoft (R) C/C++ Optimizing Compiler Version 18.00.40209
for Microsoft (R) .NET Framework version 4.00.30319.34014
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\WinCComp\binaries.x86chk\bin\i386\cl.exe:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c1.dll:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c1xx.dll:      Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c2.dll:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\link.exe:      Version 12.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\mspdb120.dll:  Version 12.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\1033\clui.dll: Version 18.00.40209.0
 Common Language Runtime:                            Version  4.00.30319.34014

cl : Command line error D8003 : missing source filename
```

Zkopírujte a vložte na celou výstupu do sestavy.

### <a name="the-command-line"></a>Příkazový řádek

Potřebujeme úplný příkazový řádek (cl.exe a jeho argumenty) sloužící k vytvoření kódu tak, aby jsme můžete vytvořit úplně stejně, jako na našem počítače. To je důležité, protože problému, který byla zjištěna může existovat pouze při sestavení s argumentem nebo kombinace argumentů.

Nejlepší místo k najít tyto informace se v protokolu sestavení ihned po se problém. Tím se zajistí, že příkazový řádek obsahuje přesně stejné argumenty, které mohou způsobovat tento problém.

#### <a name="to-report-the-contents-of-the-command-line"></a>Tak, aby odesílaly obsah příkazového řádku

1. Vyhledejte **CL.command.1.tlog** souborů a otevřete ji. Ve výchozím nastavení, tento soubor nachází ve \\...\Visual Studio *verze*\Projects\\*název řešení SolutionName*\\*ProjectName*\ Konfigurace\\*ProjectName*.tlog\CL.command.1.tlog.

   Uvnitř tohoto souboru najdete v ní názvy soubory zdrojového kódu, za nímž následuje argumenty příkazového řádku používá ke kompilaci je každý na samostatné řádky.

1. Vyhledejte řádek, který obsahuje název souboru zdrojového kódu, kde k problému dochází; na řádku pod ním obsahuje příkaz odpovídající cl.exe a jeho argumenty.

Zkopírujte a vložte celý příkazového řádku do sestavy.

### <a name="a-description-of-the-problem"></a>Popis problému

Potřebujeme podrobný popis problému, který jste došlo tak, aby bylo možné ověřit, že vidíte stejného efektu na našem počítačích; jeho také někdy užitečné pro nám vědět, co jste se pokoušeli provést a co jste očekávali.

Zadejte prosím přesné chybové zprávy, které poskytují sadu nástrojů, stručný popis, co jste se pokoušeli provést, chcete-li Pomozte nám srozumitelná kódu zkopírujte a další podrobnosti, které nám mohou pomoci diagnostikovat problém došlo, například všechny dokumentovat můžete může mít nalezen. Vyhněte se opakují. informace o nacházejí jinde v sestavě.

### <a name="the-repro"></a>Postup

Potřebujeme *zkopírujte*, příklad nezávislý zdrojového kódu, který ukazuje problém byla zjištěna, takže jsme chybu reprodukovat na našem počítače. Druh problému, které zaznamenáte určí, jaký druh zkopírujte by měla obsahovat v sestavě. Bez odpovídající postup máme nic k prozkoumání.

Krátký, úplný a samostatný repros může přímo zahrnutý v textu sestavy, ale větší repros zdrojový kód by měl být připojen sestavy. Repros, které nelze zmenšit na jediném souboru kódu musí být zabalené komprimací adresáře, který obsahuje všechny soubory do souboru .zip nebo podobné a připojené k sestavě. Žádné další podrobnosti o konkrétní scénáře by měl být vždy součástí textu sestavy, nikdy ve zdrojovém kódu.

Je nejlepší druh zkopírujte můžete případně zadat *minimální zkopírujte*. Toto je jediná, úplný a samostatný soubor zdrojového kódu (bez odkazy na uživatele hlavičky) obsahující akorát kódu k předvedení problém. Pokud zadáte postup v tomto formuláři, připojte k sestavy; právě souboru zdrojového kódu všechny, jeho, kterou potřebujeme.

Pokud problém minimální nepodařilo bez závislostí nelze zmenšit, naleznete v následujících částech k určení druh postup, který se má zahrnout do sestavy.

#### <a name="frontend-parser-crash"></a>Havárie front-endu (Analyzátor)

Front-endu havárií dojde během analýzy fáze kompilátoru. Obvykle bude emitování kompilátor [závažná chyba C1001](error-messages/compiler-errors-1/fatal-error-c1001.md) a odkazovat na zdrojový kód souborové služby a řádku číslo na kterém se stala chyba; ho bude často zmínili msc1.cpp souboru, ale můžete ignorovat této jsou podrobně popsané.

Pro tento typ havárie, zadejte [zpracované zkopírujte](#preprocessed-repros).

Tady je příklad výstupu kompilátoru pro tento typ havárie:

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

#### <a name="backend_crash"></a>Havárie back-end (vytváření kódu)

Back-end havárií, ke kterým došlo během kód generování fáze kompilátoru. Obvykle bude emitování kompilátor [závažná chyba C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)a může odkaz zdrojový kód souboru a související s problémem, číslo řádku; ho bude často zmínili compiler\utc\src\p2\main.c souboru, ale tento podrobností, můžete ignorovat.

Pro tento typ havárie zadejte [zkopírujte odkaz](#link-repros) nebo, pokud používáte generování kódu v době propojování (LTCG) [zpracované zkopírujte](#preprocessed-repros) není-li. LTGC zapnuta podle `/GL` argument příkazového řádku k cl.exe.

Tady je příklad výstupu kompilátoru pro tento typ havárie, ve kterém je LTCG **není** použít. Pokud bude mít tento tvar výstupu kompilátoru by měl poskytovat [zpracované zkopírujte](#preprocessed-repros).

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

Pokud na řádku, který začíná řetězcem **vnitřní chyba KOMPILÁTORU** uvádí link.exe, nikoli cl.exe, LTCG byl povolen a měl by poskytnout [zkopírujte odkaz](#link-repros). Pokud jeho není jasné, zda LTCG byla povolena z kompilátoru chybovou zprávu, budete muset prozkoumat argumenty příkazového řádku, které jste zkopírovali z buildu protokolu v předchozím kroku pro `/GL` argument příkazového řádku.

#### <a name="linker-crash"></a>Havárie linkeru

Linkeru havárií, ke kterým došlo během fází propojení, po spuštění kompilátoru. Obvykle bude emitování linkeru [chyba Linkerů LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Pokud výstup uvádí C1001 nebo zahrnuje vytvoření kódu v době odkaz, podívejte se na [back-end (vytváření kódu) havárií](#backend_crash) místo pro další informace.

Pro tento typ havárie, zadejte [zkopírujte odkaz](#link-repros).

Tady je příklad výstupu kompilátoru pro tento typ havárie.

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

Pokud je povolená přírůstkové propojování a až po počáteční propojení, došlo k havárii (tedy až po první úplné propojení na kterých je založena následné přírůstkové propojování) také zadejte kopii objektu (.obj) a knihovny (LIB) soubory, které odpovídají pro zdrojové soubory, které byly upraveny po počáteční propojení bylo dokončeno.

#### <a name="bad-code-generation"></a>Generování chybného kódu

Generování chybného kódu je taková situace vzácná, ale nastane, když kompilátor omylem generuje nesprávný kód, který způsobí, že vaše aplikace a havárií na modulu runtime, nikoli zjišťování potíže při kompilaci. Pokud si myslíte, problém se setkáváte s výsledky v generování chybného kódu, považovat za sestavy stejné [back-end (vytváření kódu) havárií](#backend_crash).

Pro tento typ havárie zadejte [zkopírujte odkaz](#link-repros) nebo, pokud používáte generování kódu v době propojování (LTCG) [zpracované zkopírujte](#preprocessed-repros) není-li. LTGC zapnuta podle `/GL` argument příkazového řádku k cl.exe.

## <a name="generate"></a>Generování zkopírujte

Zkopírujte je příklad dokončení, úplný a samostatný kódu, která demonstruje problému, který jste reporting. Zkopírujte je **není** fragmentu kódu; musí být kompletní příklad, který vytvoří a spustí (nebo způsobem, s výjimkou chyby, vytvořené na problém se reporting). Měl by obsahovat všechny nezbytné # direktivy i pro hlavičky standardních include.

Kromě toho je dobré zkopírujte

- **Minimální.** Repros by měl být co nejmenší při stále demonstraci přesně problému, který jste se setkali. Repros nemusí být komplexní nebo realistické; jednoduchý, na bod repros je lepší. Není potřeba zahrnout kontrolní příklady kódu, který funguje, ale možná, pokud je ilustrativní; pouze ukázkový kód, který je příčinou problému je nutné.

- **Úplný a samostatný.** Repros byste neměli nepotřebné závislosti. Pokud můžete reprodukujte problém bez knihovny třetích stran, prosím učiňte. Pokud jste reprodukování problému bez jakékoli knihovny kódu (`std::out`, `printf()` jsou v pořádku), proveďte tuto akci. Snižuje množství kód, který se musí vzít v úvahu jako Přispěvatel možné tento problém je pro nás enormously užitečné.

- **Na nejnovější verzi kompilátoru.** Repros měli použít nejnovější verzi sady nástrojů, kdykoli je to možné. Velmi často bylo opraveno problémy, na které můžete narazit stále v starší verze sady nástrojů v novější verzi.

- **Kontrolovat další kompilátory**, pokud je to relevantní. Repros, které zahrnují přenosné C++ – kód by měl ověřit chování pro jiné kompilátory Pokud je to možné.

   Tento krok pomáhá určit, že jestli váš kód je správný, jako když MSVC nesouhlasí s Clang a RSZ nebo není správný, jako když MSVC, Clang a RSZ shodnou, který vytváří kódu chyby.

Níže jsou uvedeny pokyny pro generování různé druhy repros, který budete používat pro sestavy různé druhy problémů.

### <a name="preprocessed-repros"></a>Předběžně zpracované repros

Předběžně zpracované zkopírujte je jeden zdrojový soubor, který ukazuje na problém a byla vygenerována z výstupu preprocesoru jazyka C zpracováním původní zdrojový soubor. Tento proces inlines zahrnuté hlavičky odebrání závislostí na další zdroje a soubory hlaviček a také řeší makra, #ifdefs a jinými preprocesoru příkazy, které může závisí na vašem místním prostředí.

> [!NOTE]
> Všimněte si, že předběžně zpracované repros alespoň vhodné pro problémy, které může být výsledkem chyby v našich implementace standardní knihovny, protože jsme se často mají být nahrazeny naše nejnovější, probíhá implementace zobrazíte, zda již vyřešili jsme problém. V takovém případě nebudete předzpracování postup a pokud problém nelze zmenšit na jeden zdrojový soubor, balíček kódu do souboru .zip nebo podobné, nebo zvažte použití projektu zkopírujte IDE (viz [ostatní Repros](#other-repros) níže).

#### <a name="to-preprocess-a-source-code-file"></a>Chcete-li předběžné zpracování souboru zdrojového kódu

1. Na klávesnici stiskněte klávesu Windows a začněte psát `Developer Command Prompt`.

1. Vyberte **příkazový řádek vývojáře** verze, která odpovídá verzi sady Visual Studio používáte když se objeví v seznamu odpovídá.

1. V **příkazový řádek vývojáře** okně konzoly, zadejte příkaz `cl /P argumentsfilename.cpp`.

Až budete mít soubor předběžně zpracované (teď filename.i), je vhodné Ujistěte se, že stále repros problém pomocí předběžně zpracované souboru. Můžete použít `/TP` argument příkazového řádku říct cl.exe k preprocesoru krok přeskočit a pokus o zkompilovat jako obvykle.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Potvrďte, že chyba stále repros předběžně zpracované souborem

1. Na klávesnici stiskněte klávesu Windows a začněte psát `Developer Command Prompt`.

1. Vyberte **příkazový řádek vývojáře** verze, která odpovídá verzi sady Visual Studio používáte když se objeví v seznamu odpovídá.

1. V **příkazový řádek vývojáře** okně konzoly, zadejte příkaz `cl arguments /TP filename.i`.

1. Zkontrolujte, zda je problém reprodukovat.

Nakonec připojte tento zkopírujte do sestavy.

### <a name="link-repros"></a>Odkaz repros

Zkopírujte odkaz je jeden adresář obsahující artefaktů sestavení, která souhrnně ukazují problém, který nastane během odkaz, jako je například back-end havárie zahrnující generování kódu v době propojování (LTCG) nebo havárie linkeru; zahrnuté sestavení artefaktů jsou ty, které vyžaduje jako vstup, aby lze problém reprodukovat linkeru. Odkaz repros můžete snadno vytvořit pomocí zařízení, které jsou podle linkeru.

#### <a name="to-generate-a-link-repro"></a>Ke generování odkazu zkopírujte

1. Otevřete příkazový řádek a zadejte příkaz `mkdir directory` vytvořit adresář pro zkopírujte odkaz.

1. Nastavit proměnnou prostředí link_repro k adresáři, který jste právě vytvořili; Zadejte příkaz `set link_repro=directory`.

1. Pokud chcete provést sestavení z v sadě Visual Studio spustíte z příkazového řádku zadáním příkazu `devenv`. Zajistíte tak, že hodnota proměnné prostředí link_repro je viditelná pro Visual Studio.

1. Sestavit aplikaci a potvrďte, že došlo k očekávané problému.

1. Zavřete Visual Studio nyní, pokud je spuštěn v kroku 3.

1. Clear – proměnná prostředí link_repro; Zadejte příkaz`set link_repro=`

Nakonec balíček nepodařilo komprimací celý adresáře do souboru .zip nebo podobné a jeho připojení k sestavě.

### <a name="other-repros"></a>Další repros

Pokud problém nelze zmenšit na jeden zdrojový soubor nebo předběžně zpracované zkopírujte a zkopírujte odkaz nevyžaduje žádný problém, jsme prozkoumat a projekt IDE. Měli byste být minimální kódu v projektu a všechny pokyny z tohoto dokumentu se vztahuje.

Vytvořte vaše zkopírujte jako minimální IDE projekt, pak balíček komprimací celou strukturu adresáře do souboru .zip nebo podobné a jeho připojení k sestavě.

## <a name="send"></a>Způsoby odeslání sestavy

Chcete-li získat sestavu do us několika způsoby. Můžete použít předdefinované sady Visual Studio [nahlásit problém nástroj](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017), nebo [Visual Studio Community vývojáře](https://developercommunity.visualstudio.com/) stránky. Je také možné odeslat e-mail s sestavy, ale jsou upřednostněny první dvě metody. Výběr závisí na tom, jak chcete pracovat s technici, kteří budou prozkoumat sestavy a jestli chcete sledovat průběh nebo sdílení sestavy s komunitou.

> [!NOTE]
> Bez ohledu na to, jak odeslat sestavy společnost Microsoft respektuje vaše soukromí. Informace o tom, jak jsme považovat data, která můžete nám poslat najdete v tématu [Microsoft Visual Studio rodiny ochrany osobních údajů produktu](https://www.visualstudio.com/dn948229).

### <a name="use-the-report-a-problem-tool"></a>Pomocí sestavy nástroj problém

**Nahlásit problém** nástroj v sadě Visual Studio je způsob, jak uživatelům v sadě Visual Studio sestavy celou řadu problémů s několika kliknutí. Poskytuje jednoduché formulář, který můžete použít k určení podrobné informace o problému byla zjištěna a pak odeslat sestavy, aniž byste opustili prostředí IDE.

Vytváření sestav váš problém prostřednictvím **nahlásit problém** nástroj je snadný a pohodlný z prostředí IDE. Můžete k němu přístup ze záhlaví výběrem **odeslat zpětnou vazbu** ikonu vedle **Snadné spuštění** vyhledávací pole, nebo můžete najít v řádku nabídek v **pomoci**  >  **Odeslat názor** > **nahlásit problém**.

Když zvolíte-li nahlásit problém, nejprve vyhledejte komunity vývojářů pro podobné problémy. Pokud váš problém byla nahlášena před, upvote tématu a přidejte komentář s další podrobnosti. Pokud nevidíte podobný problém, vyberte **problém nové sestavy** tlačítko v dolní části zpětnou vazbu Visual Studio dialogové okno a postupujte podle kroků zprávu o problému.

### <a name="use-the-visual-studio-developer-community-pages"></a>Pomocí stránky komunity vývojářů Visual Studio

Visual Studio Community vývojáře stránky jsou jiné pohodlný způsob, jak odesílat zprávy o problémech a najděte řešení pro Visual Studio, C++ kompilátoru, nástroje a knihovny. [Visual Studio otázky](https://developercommunity.visualstudio.com/spaces/8/index.html) stránky je tam, kde k hlášení problémů s IDE nebo instalace. Pro problémy s používáním C++ kompilátoru, linkeru a další nástroje a knihovny, [C++ otázky](https://developercommunity.visualstudio.com/spaces/62/index.html) stránky.

Do komunity vývojářů je informační zpráva v horní části každé stránce vyhledávací pole, které můžete použít k vyhledání příspěvcích nebo témata, která odesílat zprávy o problémech, které vám podobnou. Můžete zjistit, že řešení a další užitečné informace týkající se váš problém již k dispozici v existující téma. Pokud někdo ohlásil ke stejnému problému před, upvote a komentáře v tomto tématu místo vytvoření nové sestavy problém.

Pokud váš problém nebyla hlášena před, vyberte **nahlásit problém** tlačítko vedle do vyhledávacího pole na stránce komunity vývojářů. Můžete být vyzváni k přihlášení k účtu sady Visual Studio a vyjádřete umožnit přístup k aplikaci komunity vývojářů k profilu. Pokud jste přihlášeni, přejdete přímo na stránku kde můžete nahlásit problém. Můžete zahrnout kódu zkopírujte a příkazového řádku, snímky obrazovky, odkazy na související diskusí a další informace, které si myslíte, že je relevantní a užitečné.

### <a name="send-an-email"></a>Odeslat E-mail

E-mailu je další způsob k odeslání zprávy přímo do týmu Visual C++. Můžete kontaktovat nás na adrese [ compilercrash@microsoft.com ](mailto:compilercrash@microsoft.com). Tuto metodu použijte pouze v případě, že další dvě nejsou k dispozici, protože e-mailu není sledována úzce problémy hlášené do komunity vývojářů pomocí **nahlásit problém** nejsou nástroj nebo webové stránky a komentářů a řešení viditelné pro ostatní uživatelé v sadě Visual Studio.

Pokud si zvolíte sestavu odeslat e-mailem, můžete použít následující šablonu jako text e-mailové zprávy. Nezapomeňte si připojit zdrojový kód nebo další soubory, pokud nejsou včetně těchto informací v obsahu e-mailu.

```Example
To: compilercrash@microsoft.com
Subject: Visual C++ Error Report
-----

Compiler version:

CL.EXE command line:

Problem description:

Source code and repro steps:

```

> [!TIP]
> Pro jiné druhy problémů, ke kterým může dojít v sadě Visual Studio, které nesouvisí se sada nástrojů (například uživatelského rozhraní problémy, porušený funkce IDE nebo dojde k obecné chybě) může být sestava nástroj problém hlavně dobrou volbou z důvodu možnosti snímek obrazovky a jeho schopnosti záznamu akcí uživatelského rozhraní, které vést k problému byla zjištěna. Měli byste nikdy nahlásit tyto jiné typy chyb zasláním e-mailu compilercrash@microsoft.com.

