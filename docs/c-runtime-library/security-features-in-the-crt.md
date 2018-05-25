---
title: Funkce zabezpečení v CRT | Microsoft Docs
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
ms.openlocfilehash: 8195e9a7e37ac9fa9186118889d7717698d2b784
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
---
# <a name="security-features-in-the-crt"></a>Funkce zabezpečení v CRT
Mnoho staré funkcí CRT má bezpečnější, novější verze. Pokud existuje zabezpečené funkce, na méně bezpečné, starší verzi je označen jako zastaralý a obsahuje novou verzi `_s` přípony ("zabezpečení").  
  
 V tomto kontextu "zastaralé" právě znamená, že použití funkce se nedoporučuje; neznamená, že má být odebrán z CRT naplánován funkce.  
  
 Zabezpečení funkce, zabránit nebo opravte chyby zabezpečení; Místo toho budou zpracovávat chyby, když k nim dojde. Provádějí další kontroly pro chybové podmínky, a v případě chybu, jejich vyvolat obslužnou rutinu chyby (viz [ověření parametru](../c-runtime-library/parameter-validation.md)).  
  
 Například `strcpy` funkce nemá možnost nijak sdělit, pokud řetězec, který je kopírování je příliš dlouhý pro jeho cílová vyrovnávací paměť. Však jeho protějšku zabezpečené `strcpy_s`, trvá velikost vyrovnávací paměti jako parametr, takže ho můžete zjistit, zda přetečení vyrovnávací paměti dojde. Pokud používáte `strcpy_s` chcete zkopírovat 11 znaků do vyrovnávací paměti deset znak, který chybu z vaší strany; `strcpy_s` nelze opravte chybu, ale může zjišťovat vaše chyba a vás informují o tom vyvoláním obslužná rutina neplatný parametr.  
  
## <a name="eliminating-deprecation-warnings"></a>Odstranění upozornění na zastaralost  
 Odstranit zastaralá upozornění pro funkce starší, méně bezpečné několika způsoby. Nejjednodušší je jednoduše zadat `_CRT_SECURE_NO_WARNINGS` nebo použít [upozornění](../preprocessor/warning.md) – Direktiva pragma. Buď zakáže upozornění na zastaralost, ale samozřejmě stále existují problémy zabezpečení, které způsobily upozornění. Je mnohem lepší nechte vyřazení upozornění povolené a využívat nové funkce zabezpečení CRT.  
  
 V jazyce C++ je nejjednodušší způsob, jak to udělat pomocí [přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md), což v mnoha případech odstraní upozornění na zastaralost nahrazením volání zastaralé funkcí volání do nové bezpečné verze těchto funkcí. Zvažte například to zastaralé volání `strcpy`:  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 Definování `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 eliminuje upozornění změnou `strcpy` volat na `strcpy_s`, aby se zabránilo přetečení vyrovnávací paměti. Další informace najdete v tématu [přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md).  
  
 Pro tyto nepoužívané funkce bez přetížení zabezpečení šablony výborný zvažte ruční aktualizace kódu pro použití zabezpečeného verzí.  
  
 Jiný zdroj upozornění na zastaralost, který nesouvisí se zabezpečení, je funkce POSIX. Nahraďte názvy funkcí POSIX jejich ekvivalenty u standardní (například změnit [přístup](../c-runtime-library/reference/access-crt.md) k [_access –](../c-runtime-library/reference/access-waccess.md)), nebo zakáže upozornění související s POSIX vyřazení definováním `_CRT_NONSTDC_NO_WARNINGS`. Další informace najdete v tématu [kompatibility](compatibility.md).  
  
## <a name="additional-security-features"></a>Další funkce zabezpečení  
 Některé funkce zabezpečení zahrnují následující:  
  
-   `Parameter Validation`. Parametry předané do funkcí CRT se ověřují v obou zabezpečené funkce a v předchozích verzích funkce. Tyto ověření patří:  
  
    -   Kontrola **NULL** hodnoty předané funkcím.  
  
    -   Kontrola výčtové hodnoty pro platnosti.  
  
    -   Kontroluje, zda jsou celočíselné hodnoty v platném rozsahu.  
  
-   Další informace najdete v tématu [ověření parametru](../c-runtime-library/parameter-validation.md).  
  
-   Obslužná rutina pro neplatné parametry je také přístupné pro vývojáře. Při zjištění neplatný parametr, místo uplatňování a ukončení aplikace, CRT poskytuje způsob, jak tyto problémy s zkontrolujte [_set_invalid_parameter_handler –, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)funkce.  
  
-   `Sized Buffers`. Zabezpečení funkce vyžadují, aby velikost vyrovnávací paměti předat všechny funkce, která zapisuje do vyrovnávací paměti. Bezpečné verze ověřit, zda vyrovnávací paměť dostatečně velké na to před zápisem, pomáhá zabránit chybám přetečení nebezpečná vyrovnávací paměti, které by se mohl spuštění škodlivého kódu. Tyto funkce obvykle vrátit `errno` typ kód chyby a vyvolat obslužnou rutinu neplatný parametr, pokud je příliš malá velikost vyrovnávací paměti. Funkce, které čtou ze vstupní vyrovnávací paměti, jako například `gets`, mají zabezpečené verze, které vyžadují, abyste zadat maximální velikost.  
  
-   `Null termination`. Některé funkce, které zbývajících potenciálně bez řetězce ukončené mít zabezpečené verze, které zajišťují, že řetězce jsou správně ukončené hodnotou null.  
  
-   `Enhanced error reporting`. Zabezpečení funkce návratové kódy chyb s další informace o chybě, než bylo k dispozici s dříve existující funkce. Zabezpečení funkce a mnoho dříve existující funkce nastaví `errno` a často vrátit `errno` code typ je také možné, zajistit lepší zasílání zpráv o chybách.  
  
-   `Filesystem security`. Zabezpečený soubor vstupně-výstupních operací rozhraní API pro podporu zabezpečeného souboru přístup v případě, že výchozí.  
  
-   `Windows security`. Zabezpečení procesu rozhraní API vynutit zásady zabezpečení a umožňují seznamy ACL zadat.  
  
-   `Format string syntax checking`. Neplatné řetězce jsou zjištěny, například pomocí nesprávný typ pole znaků `printf` řetězce formátu.  
  
## <a name="see-also"></a>Viz také  
 [Ověření parametru](../c-runtime-library/parameter-validation.md)   
 [Přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md)   
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)