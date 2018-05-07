---
title: Chyba linkerů Lnk2001 | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78dc0c0a3a030ecb88d7138484e2c64e145f69ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2001"></a>Chyba linkerů LNK2001
nerozpoznané externí symbol "*symbol*"  
  
Zkompilovaný kód vytvoří odkaz nebo volání *symbol*, ale tento symbol není definován v některé z knihovny nebo zadané linkeru soubory objektu.  
  
Tato chybová zpráva je následován závažná chyba [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Je nutné opravit chyby všechny LNK2001 a LNK2019 opravit chyby LNK1120.  
  
## <a name="possible-causes"></a>Možné příčiny  
  
Existuje mnoho způsobů, jak tato chyba, ale všechny z nich zahrnuje odkaz na funkce nebo proměnná, která nelze linkeru *vyřešit*, nebo najít definici. Symbol není možné určit kompilátor *deklarovaný*, ale není při není *definované*, protože definice může být v různých zdrojového souboru nebo knihovny. Pokud symbol je uvedené, ale nikdy definované, linkeru, vygeneruje se chyba.  
  
### <a name="coding-issues"></a>Kódování problémy  
  
Tato chyba může být způsobeno neodpovídající velká písmena v zdrojový kód nebo definice modulu (.def) souboru. Například pokud použijete název proměnné `var1` v jazyce C++ jeden zdroj souborů a pokuste se k němu jako přístup `VAR1` na jiné, je generována tato chyba. Chcete-li tento problém vyřešit, použijte konzistentně napsaný a použita názvy.  
  
Tato chyba může být způsobena v projektu, který používá [vložené funkce](../../error-messages/tool-errors/function-inlining-problems.md) Pokud definujete funkce v zdrojového souboru, ne v záhlaví souboru. Vložená funkce je mimo zdrojový soubor, který definuje je nemohou vidět. Chcete-li tento problém vyřešit, definujte vložená funkce v hlavičkách, kde jsou deklarovány.  
  
K této chybě může dojít, pokud volat funkci C z programu C++ bez použití `extern "C"` deklaraci pro funkce C. Kompilátor používá jiný interní symbol zásady vytváření názvů pro kód C a C++ a je název interní symbol, který linkeru hledá při rozpoznávání symboly. Chcete-li tento problém vyřešit, použijte `extern "C"` obálku kolem všechny deklarace funkcí jazyka C použít v kódu C++, což způsobí, že kompilátor používal interní zásady vytváření názvů jazyka C pro tyto symboly. Možnosti kompilátoru [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) a [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) způsobit kompilátoru zkompilovat soubory jako C++ nebo C, v uvedeném pořadí, bez ohledu na příponu názvu souboru. Tyto možnosti může způsobit názvy interní funkce liší od toho, co očekáváte.  
  
Tato chyba může být způsobeno pokus o odkaz funkce nebo data, která nemají externí propojení. V jazyce C++, vložené funkce a `const` dat mít vnitřní propojení, pokud není výslovně uvedeno jako `extern`. Chcete-li tento problém vyřešit, použijte explicitní `extern` deklarace na symboly uvedené mimo definující zdrojový soubor.  
  
Tato chyba může být způsobeno [chybějící tělo funkce nebo proměnná](../../error-messages/tool-errors/missing-function-body-or-variable.md) definice. Tato chyba je běžné při deklarovat, ale nemáte definice, proměnné, funkce nebo třídy do vašeho kódu. Kompilátor stačí prototyp funkce nebo `extern` deklarace proměnné generovat soubor objektu bez chyby, ale linkeru nemůže vyřešit volání funkce nebo odkaz na proměnnou, protože není místo kódu nebo proměnná – funkce vyhrazena. Chcete-li tento problém vyřešit, ujistěte se, všechny odkazované funkce a proměnné je plně definována v zdrojového souboru nebo knihovny součástí odkaz na vaši.  
  
Tato chyba může být způsobeno volání funkce, které používá typy vrátit a parametr nebo konvence volání, které neodpovídají definicím v definici funkce. V souborech C++ objektu [název decoration](../../error-messages/tool-errors/name-decoration.md) zapadá do konečné dekorované funkce název, který se používá jako symbol tak, aby odpovídaly při volání konvence volání, třída nebo obor názvů oboru a vraťte se a parametr typy funkce funkce z jiných souborů objekt se překládají. Pokud chcete tento problém vyřešit, ujistěte se, že deklarace, definice a volání funkce všechny používat stejným oborům, typy a konvence volání.  
  
Tato chyba může být způsobeno v kódu C++, když zahrnete prototyp funkce v definici třídy, ale nepodařilo [zahrnují implementace](../../error-messages/tool-errors/missing-function-body-or-variable.md) funkce a poté ji volat. Chcete-li tento problém vyřešit, nezapomeňte poskytují definice pro všechny názvem deklarované členy třídy.  
  
Tato chyba může být způsobeno pokus o volání čistou virtuální funkci z abstraktní základní třídu. Čistý virtuální funkce nemá žádnou implementaci základní třídy. Chcete-li tento problém vyřešit, zkontrolujte, zda jsou implementované všechny volat virtuální funkce.  
  
Tato chyba může být způsobeno pokusu o použití proměnná definovaná v rámci funkce ([místní proměnné](../../error-messages/tool-errors/automatic-function-scope-variables.md)) nad rámec této funkce. Chcete-li tento problém vyřešit, odeberte odkaz na proměnnou, která není v oboru nebo přesuňte proměnnou vyššího oboru.  
  
Této chybě může dojít při sestavování prodejní verze nástroje projektu knihovny ATL generovala zprávu, že kód CRT spuštění je vyžadována. Chcete-li tento problém vyřešit, proveďte jednu z následujících  
  
-   Odebrat `_ATL_MIN_CRT` ze seznamu preprocesor definuje umožňující CRT spuštění kódu mají být zahrnuty. V tématu [Obecná stránka vlastností (projekt)](../../ide/general-property-page-project.md) Další informace.  
  
-   Volání funkcí CRT, které vyžadují CRT spuštění kódu pokud je to možné, odeberte. Místo toho použijte jejich ekvivalenty Win32. Například použít `lstrcmp` místo `strcmp`. Známé funkcí, které vyžadují CRT spuštění kódu jsou některé řetězce a plovoucí funkce bodu.  
  
### <a name="compilation-and-link-issues"></a>Kompilace a odkaz problémy  
  
K této chybě může dojít, když na projekt chybí odkaz na knihovnu (. LIB) nebo objekt (. OBJ) soubor. Chcete-li tento problém vyřešit, přidejte do projektu odkaz na požadované knihovny nebo soubor objektu. Další informace najdete v tématu [soubory .lib jako vstup Linkeru](../../build/reference/dot-lib-files-as-linker-input.md).  
  
Této chybě může dojít, pokud použijete [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) nebo [/Zl](../../build/reference/zl-omit-default-library-name.md) možnosti. Když zadáte tyto možnosti, nejsou do projektu propojené knihovny, které obsahují požadované kód, není-li být výslovně zahrnuty. Chcete-li tento problém vyřešit, explicitně obsahovat všechny knihovny, které můžete použít na příkazovém řádku odkaz. Pokud uvidíte mnoho chybí CRT nebo standardní knihovny funkce názvy při použití těchto možností, explicitně zahrňte soubory CRT a standardní knihovny DLL nebo knihovny na odkaz.  

Pokud zkompilujete pomocí **/CLR** možnost, může být chybějící odkaz na .cctor. Chcete-li tento problém vyřešit, přečtěte si téma [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md) Další informace.  
  
Této chybě může dojít, pokud jste na verzi knihovny režimu při sestavení ladicí verze aplikace. Podobně pokud použijete možnosti **/MTd** nebo **/MDd** , nebo definujte `_DEBUG` a potom na odkaz na verzi knihovny, byste měli očekávat mnoho potenciální chyby definicí, mezi jiné problémy. Propojování sestavení pro vydání režimu s knihovnami ladění také způsobí, že podobné problémy. Chcete-li tento problém vyřešit, ujistěte se, pomocí knihovny ladění v sestavení pro ladění a sestavení knihovny prodejní ve vašem prodejní.  
  
Této chybě může dojít, pokud váš kód odkazoval na symbol z jedné verze knihovny, ale zadejte jinou verzi knihovny linkeru. Obecně platí nelze kombinovat soubory objektů nebo knihovny, které jsou vytvořeny pro různé verze kompilátoru. Knihovny, které jsou dodávány v nové verzi může obsahovat znaky, které nelze nalézt v knihovnách součástí předchozí verze a naopak. Chcete-li tento problém vyřešit, vytvořte objekt soubory a knihovny se stejnou verzí kompilátoru před propojením je společně.  
  
-  Nástroje &#124; možnosti &#124; projekty &#124; adresáře VC ++ dialogové okno, v části Výběr soubory knihovny, umožňuje změnit pořadí hledání knihovny. Složka Linkeru v dialogovém okně stránky vlastností projektu může obsahovat také cesty, které by mohly být aktuální.  
  
-  Tento problém se může zobrazit při instalaci novou sadu SDK (možná do jiného umístění), a pořadí hledání neaktualizuje tak, aby odkazoval na nové umístění. Za normálních okolností byste měli umístit cestu na novou sadu SDK zahrnout a lib adresáře před výchozí umístění Visual C++. Navíc projekt obsahující vložený cesty může stále bodu staré cesty, které jsou platné, ale aktuální pro nové funkce, které jsou přidávány nové verze, která je nainstalovaná do jiného umístění.  
  
-   Pokud sestavení na příkazovém řádku a vytvořili vlastní proměnné prostředí, ověřte, že cesty k nástrojům, knihovny a soubory hlaviček přejděte na konzistentní verzi. Další informace najdete v tématu [nastavit cesty a proměnných prostředí pro sestavení příkazového řádku](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
  
V současné době není standard pro [pojmenování C++](../../error-messages/tool-errors/name-decoration.md) mezi kompilátoru dodavateli nebo i mezi různými verzemi kompilátor. Proto propojení kompilovat s jinými kompilátory soubory objektů nemusí vytvořit stejné schéma pojmenování a způsobit tak chyba LNK2001.  
  
[Směšovací vložené a bez vložené zkompilovat možnosti](../../error-messages/tool-errors/function-inlining-problems.md) na jiné moduly může způsobit LNK2001. Pokud je vytvořena knihovna C++ s vložené funkce zapnutá (**/Ob1** nebo **/Ob2**), ale odpovídající soubor hlavičky popisující funkce má vložené vypnutý (žádné `inline` – klíčové slovo), tato chyba nastane. Chcete-li tento problém vyřešit, definovat funkce `inline` v záhlaví souboru zahrnout do jiné zdrojové soubory.  
  
Pokud použijete `#pragma inline_depth` kompilátoru direktivy, ujistěte se, že máte [hodnotu 2 nebo novější sady](../../error-messages/tool-errors/function-inlining-problems.md)a ujistěte se také používají [/Ob1](../../build/reference/ob-inline-function-expansion.md) nebo [/Ob2](../../build/reference/ob-inline-function-expansion.md) – možnost kompilátoru.  
  
Této chybě může dojít, pokud vynecháte odkaz při vytváření knihovny DLL určené pouze pro možnost /NOENTRY. Chcete-li tento problém vyřešit, přidejte k příkazu odkaz /NOENTRY možnost.  
  
Této chybě může dojít, pokud používáte nesprávné /SUBSYSTEM nebo/Entry nastavení ve vašem projektu. Například pokud napíšete konzolovou aplikaci a zadat /SUBSYSTEM:WINDOWS, nerozpoznané externí je generována chyba pro `WinMain`. Chcete-li tento problém vyřešit, zkontrolujte, zda že odpovídají možnosti pro typ projektu. Další informace o těchto možnostech a vstupní body, najdete v článku [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) a [/Entry](../../build/reference/entry-entry-point-symbol.md) možnosti linkeru.  
  
### <a name="exported-symbol-issues"></a>Exportovaný symbol problémy  
  
K této chybě dojde, pokud exportu uvedené v souboru .def nebyl nalezen. To může být způsobeno neexistuje, je nesprávně napsaný nebo používá C++ dekorované názvy. Soubor .def nevyžaduje dekorované názvy. Chcete-li tento problém vyřešit, odeberte nepotřebné exportuje a použijte `extern "C"` deklarace exportovaný symbolů.  
  
## <a name="what-is-an-unresolved-external-symbol"></a>Co je symbol nerozpoznané externí?  
  
A *symbol* je název funkce nebo globální proměnná interně jej využívá kompilované objektu souboru nebo knihovny. Symbol je *definované* do souboru objektu kde úložiště je přidělen globální proměnné nebo funkce, kde je umístěn zkompilovaný kód pro tělo funkce. *Externí symbol* je symbol, to je *odkazované*, tedy použít nebo volat v souboru jeden objekt, ale definovaný v jiném souboru knihovny nebo objekt. *Exportovat symbol* je ten, který je zpřístupněn veřejně objektu souboru nebo knihovny, která ho definuje. Linkeru musí *vyřešit*, nebo najít odpovídající definice pro každý externí symbol odkazuje soubor objektu v případě, že je propojena do aplikace nebo DLL. Linkeru vygeneruje chybu, když ho nelze vyřešit externí symbol hledání odpovídající exportovaný symbol v některém z propojených souborů.    
  
## <a name="use-the-decorated-name-to-find-the-error"></a>Použít upravený název Najít chybu
  
Použití kompilátoru a linkeru C++ [dekorování názvů](../../error-messages/tool-errors/name-decoration.md), také známé jako *úprava názvu*, zakódovat doplňující informace o typ proměnné nebo návratový typ, typy parametrů, oboru a volání konvence funkce v názvu symbolu. Tento upravený název je název symbol linkeru hledá přeložit externí symboly.  
  
Protože doplňující informace stane součástí názvu symbolu, může způsobit chyby odkaz Pokud deklaraci funkce nebo proměnná přesně neodpovídá definici funkce nebo proměnná. Tomu může dojít i v případě, že stejný soubor hlaviček se používá v volající kód a kód definující, pokud jiné kompilátoru příznaky jsou použitý ke zkompilování zdrojové soubory. Například můžete získat tato chyba, pokud je kód zkompilován používat `__vectorcall` konvence volání, ale propojení do knihovny, která očekává klientům pomocí výchozí `__cdecl` nebo `__fastcall` konvence volání. V takovém případě symboly neodpovídají vzhledem k tomu, že jsou různé konvence volání   
  
A pomůže vám zjistit příčinu tento druh chyby, linkeru chybová zpráva se dozvíte, jak "popisný název" název používaný v zdrojový kód a upravený název (v závorkách) pro nerozpoznané externí symbol. Nemusíte vědět, jak přeložit upravený název, abyste mohli k porovnání s další dekorované názvy. Můžete použít nástroje příkazového řádku, které jsou součástí kompilátoru k porovnání je očekávaný symbol název a název skutečný symbol:  

-   [/EXPORTUJE](../../build/reference/dash-exports.md) a [/symboly](../../build/reference/symbols.md) možnosti příkazového řádku nástroje DUMPBIN vám může pomoct zjistit, které značky jsou definovány v vaše soubory .dll a objekt nebo knihovny. Můžete použít k ověření, že exportovaný dekorované názvy odpovídají dekorované názvy linkeru vyhledávání.  
  
V některých případech může hlásit linkeru pouze upravený název pro symbol. Nástroje příkazového řádku UNDNAME můžete získat bez upraveného formu upravený název.  
  
## <a name="additional-resources"></a>Další zdroje  
  
Další informace o možných příčinách a řešení pro LNK2001, najdete v článku na Stack Overflow otázku [co je externí symbol chybu nedefinované odkaz nebo nepřeložené a jak ji opravit?](http://stackoverflow.com/q/12573816/2002113).  

