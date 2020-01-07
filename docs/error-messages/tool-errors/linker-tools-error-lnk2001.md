---
title: Chyba linkerů LNK2001
ms.date: 12/19/2019
f1_keywords:
- LNK2001
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
ms.openlocfilehash: b6d1e53d8f057ddc93e2dfde65cb951d247dfcc0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302130"
---
# <a name="linker-tools-error-lnk2001"></a>Chyba linkerů LNK2001

> Nerozpoznaný externí symbol "*symbol*"

Zkompilovaný kód provede odkaz nebo volání *symbolu*. Symbol není definován v žádném z knihoven nebo souborů objektů prohledávaných linkerem.

Tato chybová zpráva je následována závažnou chybou [linkerů LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Chcete-li opravit chybu LINKERŮ LNK1120, nejprve opravte všechny chyby LINKERŮ LNK2001 a LINKERŮ LNK2019.

Existuje mnoho způsobů, jak získat LINKERŮ LNK2001 chyby. Všechny z nich zahrnují *odkaz* na funkci nebo proměnnou, kterou linker nemůže *přeložit*, nebo najít definici pro. Kompilátor může identifikovat, kdy kód *nedeklaruje* symbol, ale ne, pokud ho *nedefinuje* . Důvodem je, že definice může být v jiném zdrojovém souboru nebo knihovně. Pokud váš kód odkazuje na symbol, ale není nikdy definován, linker vygeneruje chybu.

## <a name="what-is-an-unresolved-external-symbol"></a>Co je nevyřešený externí symbol?

*Symbol* je interní název pro funkci nebo globální proměnnou. Je to forma názvu používaného nebo definovaného v souboru kompilovaného objektu nebo v knihovně. Globální proměnná je definována v souboru objektu, kde je pro ni přiděleno úložiště. Funkce je definována v souboru objektu, kde je umístěn zkompilovaný kód pro tělo funkce. *Externí symbol* je jeden odkazovaný v jednom souboru objektu, ale je definován v jiné knihovně nebo souboru objektu. *Exportovaný symbol* je ten, který se veřejně zpřístupňuje souborem objektu nebo knihovnou, která ho definuje.

Chcete-li vytvořit aplikaci nebo knihovnu DLL, každý použitý symbol musí mít definici. Linker musí *přeložit*nebo najít definici porovnání pro, každý externí symbol, na který odkazuje každý soubor objektu. Linker vygeneruje chybu, pokud nemůže přeložit externí symbol. To znamená, že linker nemohl najít vyhovující definici exportovaného symbolu v žádném z propojených souborů.

## <a name="compilation-and-link-issues"></a>Problémy s kompilací a propojením

K této chybě může dojít:

- V případě, že v projektu chybí odkaz na knihovnu (. LIB) nebo objekt (. OBJ). Chcete-li tento problém vyřešit, přidejte do projektu odkaz na požadovaný soubor knihovny nebo objektu. Další informace naleznete v tématu [soubory LIB jako vstup linkeru](../../build/reference/dot-lib-files-as-linker-input.md).

- Pokud má projekt odkaz na knihovnu (. LIB) nebo objekt (. OBJ), který zase vyžaduje symboly z jiné knihovny. K tomu může dojít, i když nebudete volat funkce, které způsobují závislost. Chcete-li tento problém vyřešit, přidejte do projektu odkaz na jinou knihovnu. Další informace najdete v tématu [Princip klasického modelu pro propojování: přebírání symbolů pro jízdní](https://devblogs.microsoft.com/oldnewthing/20130108-00/?p=5623)část.

- Pokud používáte možnosti [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) nebo [/zl](../../build/reference/zl-omit-default-library-name.md) . Když zadáte tyto možnosti, knihovny obsahující požadovaný kód nejsou propojeny do projektu, pokud jste je nezahrnuli explicitně. Chcete-li tento problém vyřešit, explicitně Zahrňte všechny knihovny, které používáte na příkazovém řádku propojení. Pokud při použití těchto možností vidíte mnoho chybějících názvů funkcí CRT nebo standardní knihovny, explicitně do odkazu zahrňte knihovny DLL CRT a standardní knihovny DLL nebo soubory knihoven.

- Pokud kompilujete pomocí možnosti **/CLR** . Pravděpodobně chybí odkaz na `.cctor`. Další informace o tom, jak tento problém vyřešit, naleznete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).

- Pokud propojíte s knihovnami režimu vydání při sestavování ladicí verze aplikace. Podobně platí, že pokud použijete možnosti **/MTD** nebo **/MDD** nebo definujete `_DEBUG` a pak propojíte s knihovnami verzí, měli byste očekávat mnoho potenciálních nevyřešených externích typů, mimo jiné problémy. Propojení sestavení režimu vydání s knihovnami ladění také způsobuje podobné problémy. Chcete-li tento problém vyřešit, ujistěte se, že používáte knihovny ladění v sestavení ladění a v maloobchodních knihovnách v maloobchodních sestaveních.

- Pokud váš kód odkazuje na symbol z jedné verze knihovny, ale propojíte jinou verzi knihovny. Obecně není možné kombinovat soubory objektů nebo knihovny, které jsou vytvořeny pro různé verze kompilátoru. Knihovny, které jsou dodávány v jedné verzi, mohou obsahovat symboly, které nelze nalézt v knihovnách, které jsou součástí jiných verzí. Chcete-li tento problém vyřešit, sestavte všechny soubory objektů a knihovny se stejnou verzí kompilátoru předtím, než je propojíte dohromady. Další informace najdete v tématu [ C++ binární kompatibilita 2015-2019](../../porting/binary-compat-2015-2017.md).

- Pokud jsou cesty knihovny zastaralé. Dialogové okno **nástroje > možnosti > projekty > dialogovém okně Adresáře VC + +** , v rámci výběru **souborů knihovny** , umožňuje změnit pořadí hledání knihovny. Složka Linkeru v dialogovém okně stránky vlastností projektu může obsahovat také cesty, které mohou být zastaralé.

- Když je nainstalovaná nová Windows SDK (třeba do jiného umístění). Pořadí hledání knihovny musí být aktualizováno, aby odkazovalo na nové umístění. Obvykle byste měli umístit cestu k novému adresáři SDK include a lib před výchozím vizuálním C++ umístěním. Také projekt obsahující vložené cesty může stále ukazovat na staré cesty, které jsou platné, ale nejsou aktuální. Aktualizujte cesty pro nové funkce přidané novou verzí, která je nainstalovaná v jiném umístění.

- Pokud sestavíte na příkazovém řádku a vytvořili jste vlastní proměnné prostředí. Ověřte, zda cesty k nástrojům, knihovnám a hlavičkovým souborům přejdou na konzistentní verzi. Další informace najdete v tématu [Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md) .

## <a name="coding-issues"></a>Problémy s kódováním

Tato chyba může být způsobena:

- Neshodný případ ve zdrojovém kódu nebo souboru definice modulu (. def). Pokud například pojmenujte proměnnou `var1` v jednom C++ zdrojovém souboru a pokusíte se k ní přistupovat jako `VAR1` v jiné, vygeneruje se tato chyba. Chcete-li tento problém vyřešit, použijte konzistentní a použita jména.

- Projekt, který používá [vkládání funkcí](../../error-messages/tool-errors/function-inlining-problems.md) K této chybě může dojít při definování funkcí jako `inline` ve zdrojovém souboru, nikoli v hlavičkovém souboru. Vložené funkce nelze zobrazit mimo zdrojový soubor, který je definuje. Chcete-li tento problém vyřešit, definujte vložené funkce v záhlavích, kde jsou deklarovány.

- Volání funkce jazyka C z C++ programu bez použití deklarace `extern "C"` pro funkci C. Kompilátor používá jiné konvence pojmenovávání symbolů pro jazyk C++ C a kód. Interní název symbolu je to, co linker hledá při překladu symbolů. Chcete-li tento problém vyřešit, použijte `extern "C"` obálku kolem všech deklarací funkcí jazyka C používaných C++ ve vašem kódu, což způsobí, že kompilátor použije pro tyto symboly interní konvenci pojmenování v jazyce c. Možnosti kompilátoru [/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) a [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) způsobí, že kompilátor zkompiluje soubory jako C++ nebo C bez ohledu na to, jaká přípona názvu souboru je. Tyto možnosti mohou způsobit, že názvy vnitřních funkcí se liší od toho, co očekáváte.

- Pokus o odkazování na funkce nebo data, která nemají vnější propojení. V C++, vložené funkce a data `const` mají interní propojení, pokud není explicitně určeno jako `extern`. Chcete-li tento problém vyřešit, použijte explicitní deklarace `extern` pro symboly, které jsou odkazovány mimo definiční zdrojový soubor.

- [Chybějící tělo funkce nebo definice proměnné](../../error-messages/tool-errors/missing-function-body-or-variable.md) . Tato chyba je společná, pokud deklarujete, ale nedefinujete proměnné, funkce nebo třídy v kódu. Kompilátor potřebuje prototyp funkce nebo `extern` deklaraci proměnné pro vygenerování souboru objektu bez chyby, ale linker nemůže vyřešit volání funkce nebo odkaz na proměnnou, protože není k dispozici žádný kód funkce nebo vyhrazené místo proměnné. Chcete-li tento problém vyřešit, je třeba definovat každou odkazovanou funkci a proměnnou ve zdrojovém souboru nebo knihovně, kterou propojíte.

- Volání funkce, které používá typy vrácených hodnot a parametrů nebo konvence volání, které neodpovídají těm v definici funkce. V C++ souborech objektů, [dekorování názvů](../../error-messages/tool-errors/name-decoration.md) kóduje konvenci volání, třídu nebo obor názvů a návratové a parametrové typy funkce. Kódovaný řetězec se stal součástí konečného názvu dekorované funkce. Tento název používá linker k vyřešení nebo porovnávání volání funkce z jiných souborů objektů. Chcete-li tento problém vyřešit, ujistěte se, že deklarace funkce, definice a volání používají stejné obory, typy a konvence volání.

- C++kód, který zavoláte, při zahrnutí prototypu funkce do definice třídy, ale [nezahrnuje implementaci](../../error-messages/tool-errors/missing-function-body-or-variable.md) funkce. Chcete-li tento problém vyřešit, je nutné zadat definici pro všechny členy třídy, které voláte.

- Došlo k pokusu o volání čistě virtuální funkce z abstraktní základní třídy. Čistě virtuální funkce nemá žádnou implementaci základní třídy. Chcete-li tento problém vyřešit, ujistěte se, že jsou implementovány všechny nazvané virtuální funkce.

- Pokus o použití proměnné deklarované v rámci funkce ([místní proměnná](../../error-messages/tool-errors/automatic-function-scope-variables.md)) mimo rozsah této funkce. Chcete-li tento problém vyřešit, odeberte odkaz na proměnnou, která není v oboru, nebo přesuňte proměnnou do vyššího rozsahu.

- Při vytváření vydání verze projektu ATL vytvoří zprávu, že je požadován spouštěcí kód CRT. Chcete-li tento problém vyřešit, proveďte jednu z následujících akcí:

  - Odebrání `_ATL_MIN_CRT` ze seznamu preprocesoru definuje, aby bylo možné zahrnout spouštěcí kód CRT. Další informace najdete v tématu [Obecná stránka vlastností (projekt)](../../build/reference/general-property-page-project.md).

  - Pokud je to možné, odeberte volání funkcí CRT, které vyžadují spouštěcí kód CRT. Místo toho použijte své ekvivalenty Win32. Použijte například `lstrcmp` místo `strcmp`. Známé funkce, které vyžadují spouštěcí kód CRT, jsou některé z funkcí řetězce a plovoucí desetinné čárky.

## <a name="consistency-issues"></a>Problémy konzistence

V současné době není k dispozici žádný standard pro [ C++ dekoraci názvů](../../error-messages/tool-errors/name-decoration.md) mezi dodavateli kompilátoru nebo dokonce mezi různými verzemi stejného kompilátoru. Soubory objektů kompilované s různými kompilátory nemůžou používat stejné schéma pojmenování. Jejich propojení může způsobit chybu LINKERŮ LNK2001.

[Kombinování vložených a nevložených možností kompilace](../../error-messages/tool-errors/function-inlining-problems.md) v různých modulech může způsobit linkerů LNK2001. Pokud se C++ vytvoří knihovna se zapnutým vkládáním funkcí ( **/OB1** nebo **/Ob2**), ale odpovídající hlavičkový soubor s popisem funkcí je vypnutý (žádné klíčové slovo `inline`), dojde k této chybě. Chcete-li tento problém vyřešit, definujte funkce `inline` v hlavičkovém souboru, který jste zahrnuli do jiných zdrojových souborů.

Použijete-li direktivu `#pragma inline_depth` kompilátoru, ujistěte se, že jste nastavili [hodnotu 2 nebo vyšší](../../error-messages/tool-errors/function-inlining-problems.md), a ujistěte se, že jste také použili možnost kompilátoru [/OB1](../../build/reference/ob-inline-function-expansion.md) nebo [/Ob2](../../build/reference/ob-inline-function-expansion.md) .

K této chybě může dojít, Pokud vynecháte možnost propojení/NOENTRY při vytváření knihovny DLL obsahující pouze prostředky. Chcete-li tento problém vyřešit, přidejte do příkazu Link možnost/NOENTRY.

K této chybě může dojít, pokud v projektu použijete nesprávná nastavení/SUBSYSTEM nebo/ENTRY. Například pokud napíšete konzolovou aplikaci a zadáte/SUBSYSTEM: WINDOWS, vygeneruje se nerozpoznaná externí chyba pro `WinMain`. Chcete-li tento problém vyřešit, ujistěte se, že odpovídáte možnostem typu projektu. Další informace o těchto možnostech a vstupních bodech naleznete v možnostech linkeru [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) a [/entry](../../build/reference/entry-entry-point-symbol.md) .

## <a name="exported-def-file-symbol-issues"></a>Problémy se symboly exportovaných souborů. def

K této chybě dojde, pokud se nenalezne export uvedený v souboru. def. Důvodem může být to, že export neexistuje, je nesprávně zadán nebo používá C++ dekorované názvy. Soubor. def neprovádí dekorované názvy. Chcete-li tento problém vyřešit, odeberte nepotřebné exporty a použijte `extern "C"` deklarace pro exportované symboly.

## <a name="use-the-decorated-name-to-find-the-error"></a>K nalezení chyby použijte upravený název.

Kompilátor a linker používají [dekoraci názvů](../../error-messages/tool-errors/name-decoration.md), označované také jako *pojmenování názvů.* C++ Dekorování názvů kóduje Další informace o typu proměnné v názvu symbolu. Název symbolu funkce zakóduje svůj návratový typ, typy parametrů, rozsah a konvence volání. Toto dekorické jméno je název symbolu, který linker hledá, aby vyřešil externí symboly.

Pokud se deklarace funkce nebo proměnné *přesně* neshoduje s definicí funkce nebo proměnné, může dojít k chybě odkazu. To je proto, že žádný rozdíl se bude součástí názvu symbolu, aby odpovídal. K chybě může dojít i v případě, že se stejný hlavičkový soubor používá jak v kódu volajícího, tak i v definujícím kódu. Jedním ze způsobů, jak se může stát, je, že kompilujete zdrojové soubory pomocí různých příznaků kompilátoru. Například pokud je váš kód zkompilován, aby používal konvenci volání `__vectorcall`, ale odkazujete na knihovnu, která očekává, že klienti budou volat pomocí výchozí `__cdecl` nebo `__fastcall` konvence volání. V takovém případě se symboly neshodují, protože se liší konvence volání.

Aby bylo možné najít příčinu, chybová zpráva zobrazuje dvě verze názvu. Zobrazuje "popisný název", název použitý ve zdrojovém kódu a dekorované jméno (v závorkách). Nemusíte znát, jak interpretovat dekorovaný název. Stále můžete hledat a porovnat je s jinými dekorovanými názvy. Pomocí nástrojů příkazového řádku můžete najít a porovnat očekávaný název symbolu a skutečný název symbolu:

- Možnosti [/EXPORTS](../../build/reference/dash-exports.md) a [/Symbols](../../build/reference/symbols.md) nástroje příkazového řádku DUMPBIN jsou užitečné tady. Můžou vám pomůžou zjistit, které symboly jsou definované v souboru. dll a objektu nebo knihovně. Seznam symboly lze použít k ověření, že exportované dekorované názvy odpovídají dekorovaným názvům, které linker vyhledává.

- V některých případech může linker nahlásit pouze dekorovaný název pro symbol. Pomocí nástroje příkazového řádku UNDNAME můžete získat neupravenou formu dekorované názvu.

## <a name="additional-resources"></a>Další materiály a zdroje informací

Další informace najdete v Stack Overflow otázce ["Co je nedefinovaná reference/nevyřešená chyba externího symbolu a jak ji mám opravit?"](https://stackoverflow.com/q/12573816/2002113).
