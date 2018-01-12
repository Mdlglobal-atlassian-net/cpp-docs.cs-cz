---
title: "Osvědčené postupy zabezpečení pro jazyk C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: securitybestpracticesVC
dev_langs: C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
caps.latest.revision: "45"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f1474f44b81a95c119a405dda8a91db62a08417
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="security-best-practices-for-c"></a>Doporučené postupy zabezpečení pro jazyk C++
Tento článek obsahuje informace o nástrojích zabezpečení a postupy. Jejich používání není zpřístupnit aplikace útokům imunní, ale umožňuje méně pravděpodobné, že úspěšné útoky.  
  
## <a name="visual-c-security-features"></a>Funkce zabezpečení Visual C++  
 Tyto funkce zabezpečení jsou součástí Visual C++ kompilátoru a linkeru:  
  
 [/ Guard (povolení ochrany toku řízení)](../build/reference/guard-enable-control-flow-guard.md)  
 Způsobí, že kompilátor k analýze tok řízení pro cíle nepřímé volání při kompilaci a potom pro vložení kódu k ověření cílů v době běhu.  
  
 [/GS (Kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md)  
 Dá pokyn kompilátoru vložení zjištění přetečení kódu do funkce, které jsou na riziko zneužití. Když se detekuje překročení, provádění je zastavena. Ve výchozím nastavení je tato možnost je na.  
  
 [/ SAFESEH (bitová kopie má bezpečné obslužné rutiny výjimek)](../build/reference/safeseh-image-has-safe-exception-handlers.md)  
 Dá pokyn linkeru pro zahrnutí do bitové kopie výstupní tabulku, která obsahuje adresu každé obslužné rutiny výjimky. V době běhu operačního systému používá tuto tabulku a ujistěte se, že jsou spuštěny pouze potřebné výjimky obslužné rutiny. To pomáhá zabránit spuštění obslužné rutiny výjimek, které jsou zavedené službou napadením se zlými úmysly za běhu. Tento parametr je standardně vypnutý.  
  
 [/ NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (kompatibilní s předcházením spuštění dat)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)  
 Tyto kompilátoru a linkeru možnosti umožňují kompatibility Zabránění spuštění dat (DEP). Zabránění spuštění dat chrání procesor před provádění jiných znakové stránky.  
  
 [/ analyze (Analýza kódu)](../build/reference/analyze-code-analysis.md)  
 Tato možnost kompilátoru aktivuje analýza kódu, která generuje sestavy možné problémy zabezpečení, jako je přetečení vyrovnávací paměti, zrušení inicializovaného paměť, vyhodnocení ukazatele null a nevracení paměti. Tento parametr je standardně vypnutý. Další informace najdete v tématu [analýzy kódu pro C/C++ – přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
 [/ DYNAMICBASE (použít adresu místa rozložení náhodné)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)  
 Tato možnost linkeru umožňuje vytvářet spustitelné bitové kopie, který lze načíst v různých umístěních v paměti na začátku spuštění. Tato možnost také vytváří zásobníku umístění v paměti mnohem méně předvídatelný.  
  
## <a name="security-enhanced-crt"></a>Rozšířené zabezpečení CRT  
 Knihovny za běhu C (CRT) má rozšíření, zahrnující bezpečné verze funkcí, které představují bezpečnostní rizika – například nezaškrtnuté `strcpy` řetězec kopírování. Protože starší, nebezpečné verze tyto funkce jsou zastaralé, způsobí kompilaci upozornění. Doporučujeme vám používat zabezpečený verze těchto funkcí CRT místo potlačení upozornění kompilace. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="safeint-library"></a>SafeInt – knihovna  
 [SafeInt – knihovna](../windows/safeint-library.md) pomáhá zabránit přetečení celé číslo a dalších zneužití chyb, které můžou nastat, když aplikace provede matematické operace. `SafeInt` Knihovna obsahuje [SafeInt – třída](../windows/safeint-class.md), [SafeIntException – třída](../windows/safeintexception-class.md)a několik [funkce jazyka SafeInt](../windows/safeint-functions.md).  
  
 `SafeInt` Třída chrání před přetečení celé číslo a zneužití dělení nulou. Můžete ji zpracovat porovnání mezi hodnoty různých typů. I poskytuje dvě zásady pro zpracování chyby. Výchozí zásada je určená pro `SafeInt` třídy throw `SafeIntException` třídy výjimky do sestavy, proč matematickém operaci nelze dokončit. Druhá zásada je určená pro `SafeInt` třída zastavit spuštění programu. Můžete také definovat vlastní zásadu.  
  
 Každý `SafeInt` funkce chrání jeden matematické operace z využitelných chyby. Můžete vytvořit dva různé druhy parametry bez převádění do stejného typu. Chcete-li chránit více matematické operace, použijte `SafeInt` třídy.  
  
## <a name="checked-iterators"></a>Checked – iterátory  
 Zaškrtnutý iterátor vynucuje hranice kontejneru. Ve výchozím nastavení když zaškrtnutý iterátor je mimo rozsah, generuje výjimku a končí spuštění programu. Zaškrtnutý iterátor poskytuje další úrovně odpovědi, které závisí na hodnotách, které jsou přiřazeny k preprocesor definuje jako  **\_zabezpečeného\_SCL\_VYVOLÁ** a  **\_ITERATOR\_ladění\_úroveň**. Například na  **\_ITERATOR\_ladění\_úroveň = 2**, zaškrtnutý iterátor poskytuje komplexní kontroly správnosti v režimu ladění, které jsou k dispozici pomocí nepodmíněných výrazů. Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) a [ \_ITERATOR\_ladění\_úroveň](../standard-library/iterator-debug-level.md).  
  
## <a name="code-analysis-for-managed-code"></a>Analýza kódu pro spravovaný kód  
 Analýza kódu pro spravovaný kód, také známé jako FxCop kontroluje sestavení pro shodu pokynů pro návrh rozhraní.NET Framework. FxCop analyzuje kód a metadata v každé sestavení zkontrolujte výskyt závad v těchto oblastech:  
  
-   Knihovna návrhu  
  
-   Lokalizace  
  
-   Zásady vytváření názvů  
  
-   Výkon  
  
-   Zabezpečení  
  
## <a name="windows-application-verifier"></a>Ověřovatel aplikací systému Windows  
 Ověřovač aplikace (nástroj Ověřovatel aplikací) můžete identifikovat potenciální problémy kompatibility, stability a zabezpečení aplikací.  
  
 Nástroj Ověřovatel aplikací sleduje, jak aplikace používá operační systém. Sleduje systém souborů, registr, paměti a rozhraní API aplikace běží, a doporučuje zdrojového kódu opravy pro problémy, které nalezl.  
  
 Můžete použít nástroj Ověřovatel aplikací na:  
  
-   Test potenciální chyby kompatibility aplikací, které jsou způsobeny obvyklé programovací chyby.  
  
-   Zkontrolujte aplikaci pro problémy související s pamětí.  
  s
-   Identifikujte potenciální potíže se zabezpečením v aplikaci.  
  
 Nástroj Ověřovatel aplikací je součástí sady Application Compatibility Toolkit, která je k dispozici z [kompatibilita aplikací](http://go.microsoft.com/fwlink/p/?linkid=91277) na webu TechNet.  
  

## <a name="windows-user-accounts"></a>Uživatelské účty systému Windows  
 Pomocí Windows uživatelské účty, které patří k vývojářům zpřístupňuje skupiny Administrators a--rozšíření – zákazníkům na bezpečnostní rizika. Další informace najdete v tématu [spuštění jako člen skupiny Users](running-as-a-member-of-the-users-group.md) a [jak řízení uživatelských účtů (UAC) má vliv na vaše aplikace](how-user-account-control-uac-affects-your-application.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security>   
 [Zabezpečení](/dotnet/standard/security/index)   
 [Jak nástroj Řízení uživatelských účtů (UAC) ovlivňuje vaši aplikaci](how-user-account-control-uac-affects-your-application.md)