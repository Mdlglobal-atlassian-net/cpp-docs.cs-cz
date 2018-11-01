---
title: Kompatibilita
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: f562a6a214cd1fb3feba2caf26831797d4b182fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465273"
---
# <a name="compatibility"></a>Kompatibilita

Univerzální knihovna C Run-Time (UCRT) podporuje většinu standardní knihovny jazyka C vyžaduje pro přizpůsobení C++. Implementuje knihovny C99 (ISO/IEC 9899:1999), s výjimkou makra obecný typ definovaný v \<tgmath.h > a kompatibility přísného typu v \<complex.h >. UCRT také implementuje velká podmnožina POSIX.1 (ISO/IEC 9945-1:1996 POSIX systému Application Program Interface) knihovny jazyka C, ale není plně splňující podmínky pro žádné konkrétní standard POSIX.  Kromě toho UCRT implementuje několik specifických pro společnost Microsoft funkcemi a makry, které nejsou součástí standardního.

Funkce specifické pro implementaci Microsoft Visual C++ se nacházejí v knihovně vcruntime.  Mnohé z těchto funkcí jsou pro interní použití a nemůže být volané kódem uživatele. Některé jsou popsány pro použití v ladění a provádění kompatibility.

Standard jazyka C++ vyhrazuje názvy začínající podtržítkem v globálním oboru názvů pro implementaci. Protože funkce POSIX v globálním oboru názvů, ale nejsou součástí standardní knihovny runtime jazyka C, implementace specifické pro společnost Microsoft tyto funkce mají úvodní podtržítka. Pro přenositelnost UCRT podporuje také výchozí názvy, ale kompilátor Visual C++ vyvolá upozornění na zastarání při kompilaci kódu, který je využívá. Pouze výchozí POSIX – názvy jsou zastaralé, není funkce. Chcete-li potlačit upozornění, definujte `_CRT_NONSTDC_NO_WARNINGS` před zahrnutím záhlaví v kódu, který používá původní názvy POSIX.

Některé funkce standardní knihovny jazyka C mít historii nebezpečné používání z důvodu nesprávně použitý parametry a vyrovnávací paměti není zaškrtnuto. Tyto funkce jsou často zdroj bezpečnostní problémy v kódu. Microsoft vytvořil sadu bezpečnější verze těchto funkcí, které ověřte použití parametrů a vyvolat obslužnou rutinu neplatného parametru, když se zjistí problém v době běhu.  Ve výchozím nastavení kompilátor Visual C++ problémy, zastarání upozornění, když se funkce použije, který má k dispozici bezpečnější variantu. Při kompilaci kódu jako C++ můžete definovat `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1, chcete-li odstranit většinu upozornění. Tento mechanismus využívá přetížení šablon k volání bezpečnější varianty při zachování přenosné zdrojového kódu. Chcete-li potlačit upozornění, definujte `_CRT_SECURE_NO_WARNINGS` před zahrnutím záhlaví v kódu, který používá tyto funkce. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md).

S výjimkou toho, jak je uvedeno v dokumentaci pro konkrétní funkce, je kompatibilní s rozhraním API pro Windows UCRT.  Některé funkce nejsou podporovány v aplikacích pro Windows 8 Store nebo v aplikacích pro univerzální platformu Windows (UPW) na Windows 10. Tyto funkce jsou uvedeny v [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md), což vytvoří výčet funkce není podporována modulem Windows Runtime a [UPW](/uwp).

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Aplikace pro UPW, prostředí Windows Runtime a knihovna CRT (C Run-Time)](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Popisuje, pokud rutiny UCRT nejsou kompatibilní s Universal Windows apps nebo Microsoft Store aplikace.|
|[Kompatibilita s ANSI C](../c-runtime-library/ansi-c-compliance.md)|Popisuje, CLS standardní pojmenování v UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Obsahuje pokyny pro přenesení aplikací do systému UNIX.|
|[Platformy systému Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Seznam operačních systémů, které jsou podporuje CRT.|
|[Zpětná kompatibilita](../c-runtime-library/backward-compatibility.md)|Popisuje, jak namapovat staré názvy CRT na nové značky.|
|[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)|Poskytuje přehled o soubory CRT knihovny (.lib) a možnosti kompilátoru přidružené.|