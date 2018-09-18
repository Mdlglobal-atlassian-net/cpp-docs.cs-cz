---
title: Funkce zabezpečení v CRT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99c449f9f96abbc335c58c6d46d81b55b5156c76
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023862"
---
# <a name="security-features-in-the-crt"></a>Funkce zabezpečení v CRT

Mnoho stará funkce CRT mají novějšími, bezpečnějšími verze. Pokud zabezpečené funkce existuje, starší, méně bezpečné verze je označené jako zastaralé a nová verze nemá `_s` příponu ("bezpečné").

V tomto kontextu "zastaralé" pouze znamená, že se nedoporučuje použití funkce; neznamená, že funkce je naplánováno odeberou z CRT.

Zabezpečené funkce, zabránit nebo opravte chyby v zabezpečení; Místo toho se zachytávat chyby, které se objeví. Provádějí další kontroly pro chybové podmínky, a v případě chyby, vyvolají obslužnou rutinu chyby (viz [Parameter Validation](../c-runtime-library/parameter-validation.md)).

Například `strcpy` funkce nemá možnost nijak sdělit, pokud je řetězec, který kopíruje pro jeho cílová vyrovnávací paměť příliš velký. Ale jeho zabezpečené protějšky `strcpy_s`, velikost vyrovnávací paměti jako parametr přijímá, takže ho můžete zjistit, zda přetečení vyrovnávací paměti dojde. Pokud používáte `strcpy_s` kopírování jedenáct znaků do vyrovnávací paměti deset znaků, který chybu z vaší strany; `strcpy_s` nelze opravit chybu, ale můžete zjistit chyby a poznáte tak, že vyvolá obslužnou rutinu neplatného parametru.

## <a name="eliminating-deprecation-warnings"></a>Odstranění upozornění na zastaralost

Chcete-li odstranit upozornění na zastaralost pro starší, méně zabezpečené funkce několika způsoby. Nejjednodušší je jednoduše definovat `_CRT_SECURE_NO_WARNINGS` nebo použijte [upozornění](../preprocessor/warning.md) direktivy pragma. Buď zakáže upozornění na zastaralost, ale samozřejmě stále existují problémy se zabezpečením, které způsobily upozornění. Je mnohem lepší ponechte vyřazení upozornění povolená a mohli využívat nové funkce zabezpečení CRT.

V jazyce C++, je nejjednodušší způsob, jak to udělat pomocí [přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md), což je v mnoha případech dojde k odstranění upozornění na zastaralost nahrazením volání zastaralé funkce volání nové bezpečné verze těchto funkcí. Zvažte například toto volání zastaralé `strcpy`:

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Definování `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 eliminuje upozornění tak, že změníte `strcpy` volání `strcpy_s`, což zabraňuje přetečení vyrovnávací paměti. Další informace najdete v tématu [přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md).

Pro tyto zastaralé funkce bez přetížení zabezpečení šablony byste měli jednoznačně zvážit ruční aktualizace kód Refaktorovat pro použití bezpečné verze.

Dalším zdrojem tohoto upozornění na zastaralost, nesouvisející se zabezpečením, je funkce POSIX. Nahraďte názvy funkcí POSIX ekvivalenty standardní (například změnit [přístup](../c-runtime-library/reference/access-crt.md) k [_přístupový](../c-runtime-library/reference/access-waccess.md)), nebo zakáže upozornění na zastaralost týkající se specifikace POSIX definováním `_CRT_NONSTDC_NO_WARNINGS`. Další informace najdete v tématu [kompatibility](compatibility.md).

## <a name="additional-security-features"></a>Další funkce zabezpečení

Některé funkce zabezpečení zahrnují následující:

- `Parameter Validation`. Parametry předané do funkce CRT se ověřují v obou zabezpečené funkce a v předchozích verzích funkce. Tyto ověření patří:

   - Kontrola **NULL** hodnoty předané funkcím.

   - Kontroluje se platnost výčtové hodnoty.

   - Kontroluje se, že integrální hodnoty jsou platné rozsahy.

- Další informace najdete v tématu [Parameter Validation](../c-runtime-library/parameter-validation.md).

- Obslužná rutina neplatné parametry je také přístupné pro vývojáře. Při zjištění neplatného parametru, nikoli potvrzující a ukončení aplikace, CRT poskytuje způsob, jak tyto problémy s zkontrolujte [_set_invalid_parameter_handler – _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)funkce.

- `Sized Buffers`. Zabezpečené funkce vyžadují velikost vyrovnávací paměti být předán všechny funkce, které se zapíše do vyrovnávací paměti. Bezpečné verze ověřit, že vyrovnávací paměť je příliš velká před zápisem do ní, pomáhá zabránit chybám přetečení nebezpečné vyrovnávací paměti, které by mohlo spuštění škodlivého kódu. Obvykle vrátí tyto funkce `errno` zadejte kód chyby a vyvolat obslužnou rutinu neplatného parametru, je-li velikost vyrovnávací paměti je příliš malá. Funkce, které čtou z vstupní vyrovnávací paměti, jako například `gets`, mají bezpečné verze, které vyžadují, abyste zadat maximální velikost.

- `Null termination`. Některé funkce, které zbývá potenciálně mimo řetězec zakončený mají bezpečné verze, které zajišťují, že jsou řetězce správně zakončený hodnotou null.

- `Enhanced error reporting`. Zabezpečené funkce návratové kódy chyb s další informace o chybě, než bylo k dispozici s dříve existující funkce. Zabezpečené funkce a mnoho z předchozích funkcí teď nastavte `errno` a často vrátit `errno` kódu typu, k poskytování lepšího zasílání zpráv o chybách.

- `Filesystem security`. Zabezpečený přístup k podpoře zabezpečené souboru vstupně-výstupní operace rozhraní API ve výchozím nastavení soubor.

- `Windows security`. Zabezpečení procesu rozhraní API vynutit zásady zabezpečení a umožňují seznamy ACL zadat.

- `Format string syntax checking`. Neplatné řetězce jsou zjištěny, například pomocí nesprávného typu pole znaků `printf` řetězce formátu.

## <a name="see-also"></a>Viz také

[Ověřování parametrů](../c-runtime-library/parameter-validation.md)<br/>
[Přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md)<br/>
[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)