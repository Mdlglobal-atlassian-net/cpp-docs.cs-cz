---
title: Kompatibilita
description: Popisuje kompatibilitu knihovny Microsoft Universal C Runtime Library (UCRT) se standardní knihovnou C, POSIX, s bezpečnými CRT a aplikacemi pro Store.
ms.date: 12/06/2019
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: 39b936acc43243973c2f66ef6fc7306026cc3259
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171044"
---
# <a name="compatibility"></a>Kompatibilita

Knihovna UCRT (Universal C Run-Time Library) podporuje většinu standardní knihovny jazyka C, která je C++ požadována pro shodu. Implementuje knihovnu C99 (ISO/IEC 9899:1999) s určitými výjimkami: typ – obecná makra definovaná v \<tgmath. h > a striktní kompatibilita typů v \<Complex. h >. UCRT také implementuje velkou podmnožinu knihovny C. 1 (ISO/IEC 9945-1:1996, rozhraní systémové aplikace systému POSIX). Není ale plně v souladu s žádným konkrétním standardem POSIX. UCRT také implementuje několik funkcí a maker specifických pro společnost Microsoft, které nejsou součástí standardu.

Funkce specifické pro implementaci vizuálu C++ od Microsoftu se nacházejí v knihovně vcruntime.  Mnohé z těchto funkcí jsou pro interní použití a nemohou být volány uživatelským kódem. Některé jsou popsané pro použití při kompatibilitě ladění a implementace.

C++ Standardní rezervuje názvy, které začínají podtržítkem v globálním oboru názvů pro implementaci. Funkce subsystému POSIX i funkce knihovny modulu runtime specifické pro společnost Microsoft jsou v globálním oboru názvů, ale nejsou součástí standardní běhové knihovny jazyka C. To je důvod, proč preferované implementace těchto funkcí od Microsoftu mají počáteční podtržítko. Pro přenositelnost UCRT podporuje také výchozí názvy, ale kompilátor Microsoftu C++ vydá upozornění na vyřazení, když je kód, který je používá, zkompilován. Pouze výchozí názvy jsou zastaralé, nikoli samotné funkce. Chcete-li potlačit upozornění, definujte `_CRT_NONSTDC_NO_WARNINGS` před zahrnutím jakýchkoli hlaviček v kódu, který používá původní názvy POSIX.

Některé funkce v standardní knihovně jazyka C mají historii nebezpečného použití z důvodu nepoužívaných parametrů a nezaškrtnutých vyrovnávacích pamětí. Tyto funkce jsou často zdrojem potíží se zabezpečením v kódu. Společnost Microsoft vytvořila sadu bezpečnějších verzí těchto funkcí, které ověřují použití parametrů. Vyvolá neplatnou obslužnou rutinu parametru, když je zjištěn problém za běhu.  Ve výchozím nastavení kompilátor Microsoftu C++ vydá upozornění na vyřazení při použití funkce, která má k dispozici bezpečnější variantu. Při kompilování kódu jako C++můžete definovat `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 pro odstranění většiny upozornění. Toto makro umožňuje přetížení šablony volat bezpečnější varianty při zachování přenosného zdrojového kódu. Chcete-li potlačit upozornění, definujte `_CRT_SECURE_NO_WARNINGS` před zahrnutím jakýchkoli hlaviček v kódu, které tyto funkce používají. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md).

S výjimkou případů uvedených v dokumentaci pro konkrétní funkce je UCRT kompatibilní s rozhraním API systému Windows.  Některé funkce nejsou podporované v aplikacích pro Windows Store nebo Univerzální platforma Windows ([UWP](/uwp)). Tyto funkce jsou uvedené ve [funkcích CRT, které nejsou podporované v aplikacích Univerzální platforma Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Aplikace pro UPW, prostředí Windows Runtime a knihovna CRT (C Run-Time)](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Popisuje, pokud nejsou rutiny UCRT kompatibilní s univerzálními aplikacemi pro Windows nebo s aplikacemi Microsoft Store.|
|[Kompatibilita s ANSI C](../c-runtime-library/ansi-c-compliance.md)|Popisuje názvy kompatibilní se standardem UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Poskytuje pokyny pro přenos programů do systému UNIX.|
|[Platformy systému Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Zobrazuje seznam operačních systémů, které podporuje CRT.|
|[Zpětná kompatibilita](../c-runtime-library/backward-compatibility.md)|Popisuje, jak namapovat staré názvy CRT na nové.|
|[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)|Poskytuje přehled souborů knihovny CRT (. lib) a přidružených možností kompilátoru.|
