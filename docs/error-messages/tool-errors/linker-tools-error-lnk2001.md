---
title: Chyba linkerů LNK2001
ms.date: 05/17/2017
f1_keywords:
- LNK2001
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
ms.openlocfilehash: 824fa9108e6322b1bcf77d6c28c7fb843b743833
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808102"
---
# <a name="linker-tools-error-lnk2001"></a>Chyba linkerů LNK2001

Nerozpoznaný externí symbol "*symbol*"

Zkompilovaný kód provede odkaz nebo volání *symbol*, ale tento symbol není definovaný v některém z knihovny nebo objektových souborů zadaný v linkeru.

Tato chybová zpráva je následována závažná chyba [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Je nutné opravit všechny LNK2001 a LNK2019 chyby opravit chyby LNK1120.

## <a name="possible-causes"></a>Možné příčiny

Existuje mnoho způsobů, jak se tato chyba, ale všechny z nich zahrnuje odkaz na funkci nebo proměnnou, která linker nemůže *vyřešit*, nebo si najděte definici. Kompilátor může identifikovat při symbol nemá *deklarované*, ale ne když není *definované*, protože definice může být v odlišném zdrojovém souboru nebo knihovny. Pokud symbol je uvedené, ale dosud definováno, linker generuje chybu.

### <a name="coding-issues"></a>Chyby v kódování

Tuto chybu může způsobovat neodpovídající v takovém případě zdrojový kód nebo definice modulu (.def) souboru. Například, pokud zadáte název proměnné `var1` v jazyce C++ jednoho zdrojového souboru a zkuste se připojit jako `VAR1` v jiném, vygeneruje se tato chyba. Chcete-li vyřešit tento problém, použijte konzistentně zadány a notaci názvy.

Tato chyba může být způsobena v projektu, který používá [funkce vkládání](../../error-messages/tool-errors/function-inlining-problems.md) definujete funkce ve zdrojovém souboru, nikoli v souboru hlaviček. Vložené funkce nemohou vidět mimo zdrojového souboru, který definuje. Chcete-li vyřešit tento problém, definování vložené funkce v záhlaví, ve kterém jsou deklarovány.

Tato chyba může nastat, pokud volání funkce C z programu v jazyce C++ bez použití `extern "C"` deklarace pro funkce C. Kompilátor používá jiný interní symbol zásady vytváření názvů pro kód jazyka C a C++ a jedná se o interní symbol název, který hledá linkeru, při zpracování symbolů. Chcete-li tento problém vyřešit, použijte `extern "C"` obálku kolem všechny deklarace funkce jazyka C za použití ve vašem kódu C++, což způsobí, že kompilátor používal vnitřní zásady vytváření názvů jazyka C pro tyto symboly. Možnosti kompilátoru [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) a [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) způsobit, že kompilátor pro kompilaci souborů jako C++ nebo C, v uvedeném pořadí, bez ohledu na příponu názvu souboru. Tyto možnosti může způsobit, že názvy interní funkce liší od toho, co očekáváte.

Tuto chybu může způsobovat pokus o odkazování funkce nebo data, která nemají vnější propojení. V jazyce C++, vložené funkce a `const` data mají vnitřní propojení, pokud explicitně zadané jako `extern`. Chcete-li tento problém vyřešit, použijte explicitní `extern` deklarace na symboly uvedené mimo definiční zdrojový soubor.

Tuto chybu může způsobovat [chybí tělo funkce nebo proměnná](../../error-messages/tool-errors/missing-function-body-or-variable.md) definice. Tato chyba je běžná v případě deklarovat, ale nebudete definovat, proměnných, funkcí nebo tříd ve vašem kódu. Kompilátor potřebuje pouze prototypu funkce nebo `extern` deklarace proměnné se vygenerovat soubor objektu bez chyby, ale linkeru nelze vyřešit volání funkce nebo odkaz na proměnnou, protože není kód nebo proměnná místa – funkce vyhrazená. Chcete-li vyřešit tento problém, ujistěte se, že všechny odkazované funkce a proměnné je plně definována ve zdrojovém souboru nebo knihovny zahrnuté ve vašem odkazu.

Tuto chybu může způsobovat volání funkce, která používá typy vrácených hodnot a parametrů a konvence volání, které neodpovídají těm v definici funkce. V souborech objektů jazyka C++ [název dekorace](../../error-messages/tool-errors/name-decoration.md) zahrnuje konvence volání, obor třídy nebo oboru názvů a typy vrácených hodnot a parametrů funkce do konečné upravený funkce název, který se použije jako symbol tak, aby odpovídaly při volání funkce z jiné objektové soubory jsou vyřešeny. Chcete-li vyřešit tento problém, ujistěte se, že deklaraci, definici a volání funkce všechny používat stejné rozsahy, typy a konvence volání.

Tato chyba může být způsobena v kódu jazyka C++, když zahrnují prototypu funkce v definici třídy, ale nepovedlo se [zahrnují provádění](../../error-messages/tool-errors/missing-function-body-or-variable.md) funkce a následně ji zavolat. Chcete-li vyřešit tento problém, je potřeba poskytnout definici pro všechny volat členy třídy deklarované.

Tato chyba může být způsobeno pokus o volání čistě virtuální funkci z abstraktní základní třídu. Čistě virtuální funkce nemá žádnou implementaci základní třídy. Chcete-li vyřešit tento problém, zkontrolujte, zda jsou implementovány všechny volat virtuální funkce.

Tato chyba může být způsobena tak, že zkusíte použít proměnné deklarované v rámci funkce ([lokální proměnná](../../error-messages/tool-errors/automatic-function-scope-variables.md)) nad rámec této funkce. Chcete tento problém vyřešit, odeberte odkaz na proměnnou, která není v oboru nebo přesuňte proměnné vyššího oboru.

Této chybě může dojít při sestavování projektu ATL, verzi vytváření zprávu, že je vyžadována CRT spouštěcí kód. Chcete-li tento problém vyřešit, proveďte jednu z těchto možností

- Odebrat `_ATL_MIN_CRT` ze seznamu preprocesor definuje umožňující spouštění kódu CRT mají být zahrnuty. Zobrazit [Obecná stránka vlastností (projekt)](../../build/reference/general-property-page-project.md) Další informace.

- Pokud je to možné odeberte volání funkce CRT, které vyžadují CRT spouštěcí kód. Místo toho použijte ekvivalenty Win32. Například použít `lstrcmp` místo `strcmp`. Známých funkcí, které vyžadují CRT při spuštění kódu jsou některé řetězce a plovoucího bodu funkce.

### <a name="compilation-and-link-issues"></a>Kompilace a odkaz problémy

Této chybě může dojít, když projektu chybí odkaz na knihovnu (. LIB) nebo objekt (. Soubor OBJ). Chcete tento problém vyřešit, přidejte odkaz na soubor objektu a požadované knihovny do projektu. Další informace najdete v tématu [soubory .lib jako vstup Linkeru](../../build/reference/dot-lib-files-as-linker-input.md).

K této chybě může dojít, pokud použijete [: / NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) nebo [/Zl](../../build/reference/zl-omit-default-library-name.md) možnosti. Při zadávání těchto možností knihovny, které obsahují kódu nejsou připojeny do projektu, pokud jste výslovně zahrnuty. Chcete-li vyřešit tento problém, explicitně zahrňte všechny knihovny, které používáte na příkazový řádek propojení. Pokud se zobrazí mnoho chybějící CRT nebo standardní knihovna názvy funkcí při použití těchto možností, explicitně zahrňte soubory CRT a Standard knihoven DLL nebo knihovny v odkazu.

Pokud kompilujete pomocí **/CLR** možnost, může být chybějící odkaz na .cctor. Chcete-li vyřešit tento problém, naleznete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md) Další informace.

K této chybě může dojít, pokud můžete propojit ke knihovnám režimu vydání při sestavení ladicí verze aplikace. Podobně pokud použijete možnosti **/MTD** nebo **/MDd** nebo definovat `_DEBUG` a pak se propojit ke knihovnám vydání, měli byste očekávat, mnoho možných nerozpoznané externí typy, mezi další problémy. Propojování sestavení pro vydání režimu knihovny ladění také způsobí, že s podobnými problémy. Chcete-li vyřešit tento problém, ujistěte se, že používat knihovny ladění v sestavení ladění a sestavení knihovny maloobchodního prodeje v vašeho maloobchodního prodeje.

K této chybě může dojít, pokud váš kód odkazuje na symbol z jedné verze knihovny, ale můžete zadat jinou verzi knihovny do propojovacího programu. Obecně platí nejde kombinovat soubory objektů nebo knihoven, které jsou vytvořeny pro různé verze kompilátoru. Knihovny, které se dodávají v nové verzi může obsahovat symboly, které se nenašel v knihovnách zahrnutá v předchozích verzích a naopak. Chcete-li vyřešit tento problém, sestavujte všech souborů objektů a knihovny se zmírněními hrozeb stejnou verzi nástroje kompilátor před propojí je dohromady.

- Nástroje &#124; možnosti &#124; projekty &#124; adresáře VC ++ dialogového okna, v části Výběr soubory knihovny, umožňuje změnit pořadí hledání knihoven. Složka Linkeru v dialogové okno stránky vlastností projektu může také obsahovat cesty, které může být zastaralá.

- Tento problém se můžou objevit, když je nainstalován na novou sadu SDK (například do jiného umístění) a pořadí hledání není aktualizován tak, aby odkazoval na nové umístění. Za normálních okolností byste měli umístit cestu novou sadu SDK zahrnout a lib adresáře před Visual C++ výchozí umístění. Projekt obsahující vložené cesty může navíc stále odkazovat na staré cesty, které jsou platné, ale zastaralé pro nové funkce přidá nová verze, který je nainstalován do jiného umístění.

- Pokud sestavení na příkazovém řádku a vytvořili vlastní proměnné prostředí, ověřte, že cesty k nástrojům, knihovny a soubory hlaviček přejít na konzistentní verzi. Další informace najdete v tématu [nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

Aktuálně nejsou k dispozici žádné standard pro [C++ pojmenování](../../error-messages/tool-errors/name-decoration.md) mezi dodavateli kompilátoru nebo dokonce i mezi různými verzemi kompilátoru. Proto propojování souborů objektů kompilován jinými kompilátory nemusí vytvářejí stejné schéma pojmenování a chyba LNK2001, čímž vznikne.

[Kombinování vložené a které nejsou vložené možnosti kompilace](../../error-messages/tool-errors/function-inlining-problems.md) na různých modulů, může způsobit LNK2001. Pokud knihovnu C++ se vytvoří pomocí funkce vkládání zapnuté (**/Ob1** nebo **/ob2**), ale má odpovídající soubor záhlaví popisující funkce vkládání vypnuto (žádné `inline` – klíčové slovo), k této chybě Vyvolá se v. Chcete-li vyřešit tento problém, definování funkcí `inline` v hlavičkovém souboru je zahrnout v jiných zdrojových souborech.

Pokud používáte `#pragma inline_depth` kompilátoru direktiv, ujistěte se, že máte [hodnotu 2 nebo novější sada](../../error-messages/tool-errors/function-inlining-problems.md)a ujistěte se, že použijete také [/Ob1](../../build/reference/ob-inline-function-expansion.md) nebo [/ob2](../../build/reference/ob-inline-function-expansion.md) – možnost kompilátoru.

K této chybě může dojít, pokud vynecháte odkaz možnost NOENTRY při vytváření knihovny DLL pouze prostředků. Chcete-li vyřešit tento problém, přidejte do příkazu link/NOENTRY.

K této chybě může dojít, pokud používáte nesprávné/Subsystem nebo/Entry nastavení ve vašem projektu. Například pokud napíšeme konzolovou aplikaci a zadáte/Subsystem: Windows, nevyřešené externí bude generována chyba pro `WinMain`. Chcete-li vyřešit tento problém, ujistěte se, že odpovídat možnosti pro typ projektu. Další informace o těchto možnostech a vstupní body, najdete v článku [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) a [/Entry](../../build/reference/entry-entry-point-symbol.md) možnosti linkeru.

### <a name="exported-symbol-issues"></a>Exportovanému symbolu problémy

Tato chyba nastane, pokud nebyl nalezen export uvedené v .def souboru. Důvodem může být buď neexistuje, je nesprávně zadány nebo používá C++ dekorované názvy. Soubor .def dekorované názvy nepřijímá. Chcete tento problém vyřešit, odeberte nepotřebné exporty a pomocí `extern "C"` deklarace pro exportované symboly.

## <a name="what-is-an-unresolved-external-symbol"></a>Co je nerozpoznaný externí symbol?

A *symbol* je název funkce nebo globální proměnné interně jej využívá kompilovaný objektový soubor nebo knihovny. Symbol je *definované* do souboru objektu Pokud úložiště je alokováno pro globální proměnnou nebo funkci, ve kterém je umístí zkompilovaný kód pro tělo funkce. *Externí symbol* je symbol, která *odkazované*, to znamená, používá nebo volat v souboru jednoho objektu, ale definované v jiném souboru knihovny nebo objekt. *Exportovat symbol* je ten, který má být zpřístupněn veřejně soubor objektu nebo knihovny, který ji definuje. Propojovací program musí *vyřešit*, nebo si najděte odpovídající definice pro každý externí symbol odkazuje objektový soubor propojeného do aplikace nebo knihovny DLL. Linker dojde k chybě, když ho nelze přeložit externí symbol tím, že hledá odpovídající exportovanému symbolu v některém z propojené soubory.

## <a name="use-the-decorated-name-to-find-the-error"></a>Najít chyby pomocí upravený název

Použití kompilátoru a linkeru C++ [dekorování názvů](../../error-messages/tool-errors/name-decoration.md), označované také jako *pozměnění názvu*, určený ke kódování Další informace o typu proměnné nebo návratový typ, typy parametrů, oboru a volání konvence funkce v názvu symbolu. Tento upravený název je název symbolu propojovací program vyhledá k překladu externích symbolů.

Protože dodatečné informace bude část názvu symbolu, chyba odkazu může dojít, pokud deklarace funkce nebo proměnná přesně neodpovídá definici funkce nebo proměnná. K tomu může dojít i v případě stejného souboru hlavičky se používá v volající kód a kód definující, pokud kompilátor jiné příznaky se používají při kompilaci zdrojové soubory. Například můžete získat tuto chybu Pokud váš kód je zkompilován používat `__vectorcall` konvence volání, ale odkaz na knihovnu, která očekává, že klientům pomocí výchozí `__cdecl` nebo `__fastcall` konvence volání. V takovém případě symbolů se neshodují s vzhledem k tomu, že jsou různých konvencí volání

A umožňují najít příčinu předejít těmto chybám, linker chybová zpráva se dozvíte, jak "popisný název," název použitý v zdrojový kód a upravený název (v závorkách) pro nerozpoznaný externí symbol. Nemusíte vědět, jak převést upravený název, abyste mohli porovnat s další dekorované názvy. Můžete použít nástroje příkazového řádku, které jsou součástí kompilátoru k porovnání očekávaný symbol název a název skutečný symbol:

- [/EXPORTUJE](../../build/reference/dash-exports.md) a [/symboly](../../build/reference/symbols.md) možnosti příkazového řádku nástroj DUMPBIN vám můžou pomoct odhalit symboly, které jsou definovány v souborech DLL a objektů nebo knihoven. Můžete to ověřit, že exportovaný dekorované názvy neshoduje s dekorované názvy propojovací program vyhledá.

V některých případech linker může jenom nahlásit to upravený název pro symbol. Můžete použít nástroj příkazového řádku UNDNAME pro získání upraveného formulář upravený název.

## <a name="additional-resources"></a>Další zdroje

Další informace o možných příčinách a řešení pro LNK2001 viz otázka na Stack Overflow [co se o chybu nedefinované odkaz/nerozpoznaných externích symbolů a jak ho mám opravit?](http://stackoverflow.com/q/12573816/2002113).

