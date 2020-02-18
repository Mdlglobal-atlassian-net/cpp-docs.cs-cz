---
title: Doporučené postupy zabezpečení pro jazyk C++
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: eaaa581ff622438c2e395c34b4b026aca693a845
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416166"
---
# <a name="security-best-practices-for-c"></a>Doporučené postupy zabezpečení pro jazyk C++

Tento článek obsahuje informace o nástrojích a postupech zabezpečení. Pomocí těchto aplikací nedojde ke odolnosti proti útokům, ale díky tomu jsou úspěšné útoky méně pravděpodobný.

## <a name="visual-c-security-features"></a>Funkce C++ vizuálního zabezpečení

Tyto funkce zabezpečení jsou integrované do kompilátoru a C++ linkeru Microsoftu:

[/guard (povolení ochrany toku řízení)](../build/reference/guard-enable-control-flow-guard.md)<br/>
Způsobí, že kompilátor analyzuje tok řízení pro cíle nepřímých volání v době kompilace a pak vloží kód pro ověření cílů za běhu.

[/GS (kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md)<br/>
Instruuje kompilátor, aby vložil kód pro detekci přetečení do funkcí, které hrozí zneužít. Při zjištění překročení se spuštění zastaví. Ve výchozím nastavení je tato možnost zapnutá.

[/SAFESEH (image má bezpečné obslužné rutiny výjimek)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
Instruuje linker, aby se zahrnul do výstupního obrázku tabulka, která obsahuje adresu každé obslužné rutiny výjimky. V době běhu operační systém používá tuto tabulku k tomu, aby se zajistilo, že budou provedeny pouze legitimní obslužné rutiny výjimek. To pomáhá zabránit spuštění obslužných rutin výjimek, které jsou zavedeny škodlivým útokem v době běhu. Tento parametr je standardně vypnutý.

[/NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (kompatibilní s zabráněním spuštění dat)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md) tyto možnosti kompilátoru a linkeru umožňují kompatibilitu s funkcí Zabránění spuštění dat (DEP). DEP chrání procesor před spouštěním nekódových stránek.

[/analyze (analýza kódu)](../build/reference/analyze-code-analysis.md)<br/>
Tato možnost kompilátoru aktivuje analýzu kódu, která hlásí potenciální problémy se zabezpečením, jako je přetečení vyrovnávací paměti, neinicializovaná paměť, přesměrování ukazatele null a nevracení paměti. Tento parametr je standardně vypnutý. Další informace naleznete v tématu [Analýza kódu pro C/C++ Overview](/cpp/code-quality/code-analysis-for-c-cpp-overview).

[/DYNAMICBASE (použití modulu pro náhodné rozložení adresního prostoru)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
Tato možnost linkeru umožňuje sestavovat spustitelnou bitovou kopii, která může být načtena do různých umístění v paměti na začátku provádění. Tato možnost také způsobí, že umístění zásobníku v paměti bude mnohem méně předvídatelné.

## <a name="security-enhanced-crt"></a>Vylepšené zabezpečení CRT

Běhová knihovna jazyka C (CRT) byla rozšířena tak, aby zahrnovala zabezpečené verze funkcí, které představují bezpečnostní rizika, například funkce nezaškrtnutou `strcpy`ho kopírování řetězce. Vzhledem k tomu, že starší, nezabezpečené verze těchto funkcí jsou zastaralé, způsobují upozornění při kompilaci. Doporučujeme, abyste používali zabezpečené verze těchto funkcí CRT namísto potlačení upozornění kompilace. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="safeint-library"></a>SafeInt – knihovna

[Knihovna SafeInt](../safeint/safeint-library.md) pomáhá zabránit přetečení celých čísel a jiným zneužitým chybám, které mohou nastat, pokud aplikace provádí matematické operace. Knihovna `SafeInt` obsahuje [třídu SafeInt](../safeint/safeint-class.md), [třídu SafeIntException –](../safeint/safeintexception-class.md)a několik [funkcí SafeInt](../safeint/safeint-functions.md).

Třída `SafeInt` chrání proti přetečení celého čísla a dělení nulou. Můžete ji použít ke zpracování porovnání hodnot různých typů. Poskytuje dvě zásady zpracování chyb. Výchozí zásada je určena pro třídu `SafeInt` k vyvolání výjimky `SafeIntException` třídy, která oznamuje, proč nelze dokončit matematickou operaci. Druhá zásada je určena pro třídu `SafeInt` k zastavení provádění programu. Můžete také definovat vlastní zásady.

Každá funkce `SafeInt` chrání jednu matematickou operaci před zneužitím chyby. Můžete použít dva různé druhy parametrů bez jejich převádění na stejný typ. Chcete-li chránit více matematických operací, použijte třídu `SafeInt`.

## <a name="checked-iterators"></a>Checked – iterátory

Kontrolovaný iterátor vynutil hranice kontejneru. Ve výchozím nastavení, když je zaškrtnutý iterátor mimo hranice, vygeneruje výjimku a ukončí provádění programu. Kontrolovaný iterátor poskytuje další úrovně odezvy, které závisí na hodnotách, které jsou přiřazeny preprocesoru, například **\_zabezpečení\_sql\_vyvolá** a **\_ITERÁTOR\_ladit úroveň\_** . Například při **\_iterátoru\_ladění\_Level = 2**, kontrolovaný iterátor poskytuje komplexní kontroly správnosti v režimu ladění, které jsou zpřístupněny pomocí výrazů. Další informace najdete v tématech [kontrolované iterátory](../standard-library/checked-iterators.md) a [\_ITERÁTOR\_ladění úrovně\_](../standard-library/iterator-debug-level.md).

## <a name="code-analysis-for-managed-code"></a>Analýza kódu pro spravovaný kód

Analýza kódu pro spravovaný kód, označovaná také jako FxCop, kontroluje sestavení pro účely souladu s pokyny pro návrh the.NET Framework. FxCop analyzuje kód a metadata v každém sestavení a kontroluje nedostatky v následujících oblastech:

- Návrh knihovny

- Lokalizace

- Zásady vytváření názvů

- Výkon

- Zabezpečení

## <a name="windows-application-verifier"></a>nástroj Ověřovatel aplikací Windows

[Nástroj Ověřovatel aplikací (AppVerifier)](/windows-hardware/drivers/debugger/enable-application-verifier) vám může pomáhat identifikovat potenciální problémy s kompatibilitou aplikací, stabilitou a zabezpečením.

AppVerifier sleduje, jak aplikace používá operační systém. Sleduje systém souborů, registr, paměť a rozhraní API, když je aplikace spuštěná, a doporučuje opravy zdrojového kódu pro problémy, které se zjistí.

AppVerifier můžete použít k těmto akcím:

- Otestujte potenciální chyby kompatibility aplikací, které jsou způsobeny běžnými chybami programování.

- Prověřte aplikaci pro problémy související s pamětí.

- Identifikujte potenciální problémy se zabezpečením aplikace.

## <a name="windows-user-accounts"></a>Uživatelské účty systému Windows

Pomocí uživatelských účtů Windows, které patří do skupiny Administrators, zveřejňuje vývojáři a – podle rozšíření – zákazníci na rizika zabezpečení. Další informace najdete v tématu [spuštění jako člen skupiny Users](running-as-a-member-of-the-users-group.md) a [vliv řízení uživatelských účtů (UAC) na vaši aplikaci](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Pokyny pro spekulativní kanály na straně spuštění

Informace o tom, jak usnadní a zmírnit proti spekulativním softwarovým ohrožením zabezpečení kanálu na C++ straně služby, najdete v tématu [ C++ pokyny pro vývojáře pro spekulativní kanály na straně spuštění](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Viz také

<xref:System.Security> <br/>
[Zabezpečení](/dotnet/standard/security/index)<br/>
[Jak nástroj Řízení uživatelských účtů (UAC) ovlivňuje vaši aplikaci](how-user-account-control-uac-affects-your-application.md)
