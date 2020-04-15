---
title: Funkce zabezpečení v CRT
ms.date: 11/04/2016
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
ms.openlocfilehash: 1b42c766a7b75cb3f4d5c20d715968905d529d04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361012"
---
# <a name="security-features-in-the-crt"></a>Funkce zabezpečení v CRT

Mnoho starých funkcí CRT má novější, bezpečnější verze. Pokud existuje zabezpečená funkce, starší, méně zabezpečená verze je označena `_s` jako zastaralá a nová verze má příponu ("secure").

V tomto kontextu "zastaralé" znamená pouze, že použití funkce se nedoporučuje; neznamená, že je naplánováno odebrání funkce z CRT.

Zabezpečené funkce nezabraňují chybám zabezpečení ani je neopravují. místo toho zachycují chyby, když k nim dojde. Provádějí další kontroly chybových stavů a v případě chyby vyvolávají obslužnou rutinu chyby (viz [Ověření parametru).](../c-runtime-library/parameter-validation.md)

Například `strcpy` funkce nemá žádný způsob, jak říct, pokud řetězec, který je kopírování je příliš velký pro jeho cílové vyrovnávací paměti. Jeho zabezpečený `strcpy_s`protějšek , však bere velikost vyrovnávací paměti jako parametr, takže může určit, pokud dojde k přetečení vyrovnávací paměti. Pokud používáte `strcpy_s` ke kopírování jedenáct znaků do vyrovnávací paměti deseti znaků, je to chyba z vaší strany; `strcpy_s` nemůže opravit chybu, ale může zjistit vaši chybu a informovat vás vyvoláním neplatné obslužné rutiny parametru.

## <a name="eliminating-deprecation-warnings"></a>Eliminace varování před vyřazením

Existuje několik způsobů, jak eliminovat upozornění na vyřazení starších, méně zabezpečených funkcí. Nejjednodušší je jednoduše definovat `_CRT_SECURE_NO_WARNINGS` nebo použít [varování](../preprocessor/warning.md) pragma. Buď zakáže upozornění na vyřazení, ale samozřejmě stále existují problémy se zabezpečením, které způsobily varování. Je mnohem lepší ponechat upozornění na vyřazení povolena a využít výhod nových funkcí zabezpečení CRT.

V jazyce C++ je nejjednodušší způsob, jak to provést, použít [přetížení zabezpečené šablony](../c-runtime-library/secure-template-overloads.md), což v mnoha případech eliminuje upozornění na vyřazení nahrazením volání zastaralých funkcí voláním nových zabezpečených verzí těchto funkcí. Zvažte například toto zastaralé `strcpy`volání na :

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Definování `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 eliminuje upozornění změnou `strcpy` `strcpy_s`volání , který zabraňuje přetečení vyrovnávací paměti. Další informace naleznete [v tématu Secure Template Overloads](../c-runtime-library/secure-template-overloads.md).

Pro tyto zastaralé funkce bez přetížení zabezpečené šablony byste měli určitě zvážit ruční aktualizaci kódu tak, aby používal zabezpečené verze.

Dalším zdrojem varování vyřazení, které nesouvisí se zabezpečením, jsou funkce POSIX. Nahraďte názvy funkcí POSIX standardními ekvivalenty (například změňte [přístup](../c-runtime-library/reference/access-crt.md) k [_access](../c-runtime-library/reference/access-waccess.md)) `_CRT_NONSTDC_NO_WARNINGS`nebo definujte upozornění týkající se funkce POSIX . Další informace naleznete v [tématu Kompatibilita](compatibility.md).

## <a name="additional-security-features"></a>Další funkce zabezpečení

Některé funkce zabezpečení zahrnují následující:

- `Parameter Validation`. Parametry předávané funkcím CRT jsou ověřeny jak v zabezpečených funkcích, tak v mnoha již existujících verzích funkcí. Mezi tato ověření patří:

  - Kontrola hodnot **NULL** předaná funkcím.

  - Kontrola výčtu hodnot pro platnost.

  - Kontrola, zda jsou integrální hodnoty v platných rozsahech.

- Další informace naleznete v [tématu Ověření parametru](../c-runtime-library/parameter-validation.md).

- Obslužná rutina pro neplatné parametry je také přístupná vývojáři. Při výskytu neplatný parametr, namísto uplatnění a ukončení aplikace CRT poskytuje způsob, jak zkontrolovat tyto problémy s [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) funkce.

- `Sized Buffers`. Zabezpečené funkce vyžadují, aby velikost vyrovnávací paměti byla předána libovolné funkci, která zapisuje do vyrovnávací paměti. Zabezpečené verze ověřují, zda je vyrovnávací paměť dostatečně velká před zápisem do ní, což pomáhá zabránit nebezpečným chybám přetečení vyrovnávací paměti, které by mohly umožnit spuštění škodlivého kódu. Tyto funkce obvykle `errno` vrátí typ kódu chyby a vyvolat obslužnou rutinu neplatného parametru, pokud je velikost vyrovnávací paměti příliš malá. Funkce, které čtou ze `gets`vstupních vyrovnávacích pamětí, například , mají zabezpečené verze, které vyžadují zadání maximální velikosti.

- `Null termination`. Některé funkce, které ponechaly potenciálně neukončené řetězce, mají zabezpečené verze, které zajišťují, že řetězce jsou správně ukončeny s nulou.

- `Enhanced error reporting`. Zabezpečené funkce vracejí kódy chyb s více informacemi o chybách, než bylo k dispozici u již existujících funkcí. Zabezpečené funkce a mnoho již existujících `errno` funkcí nyní `errno` nastaveny a často vrátit typ kódu také poskytnout lepší zasílání zpráv o chybách.

- `Filesystem security`. Vstupně-nosová úložiště souborů podporuje zabezpečený přístup k souborům ve výchozím případě.

- `Windows security`. Úložiště API zabezpečeného procesu vynucují zásady zabezpečení a umožňují zadat počet přístupových kont.

- `Format string syntax checking`. Neplatné řetězce jsou zjištěny, například pomocí `printf` nesprávných znaků pole typu ve formátovacích řetězcích.

## <a name="see-also"></a>Viz také

[Ověření parametru](../c-runtime-library/parameter-validation.md)<br/>
[Zabezpečené přetížení šablony](../c-runtime-library/secure-template-overloads.md)<br/>
[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
