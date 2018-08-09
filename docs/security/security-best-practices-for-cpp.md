---
title: Osvědčené postupy zabezpečení pro jazyk C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/08/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- securitybestpracticesVC
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
author: mikeblome
ms.author: mikeblome
ms.workload:
- cplusplus
ms.openlocfilehash: e16a00d83f7917cf21f114b2a80fa1ad55a90875
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015621"
---
# <a name="security-best-practices-for-c"></a>Doporučené postupy zabezpečení pro jazyk C++

Tento článek obsahuje informace o zabezpečení nástroje a postupy. Jejich používání Nedovolte, aby byly aplikace útokům imunní, ale je méně pravděpodobné, že úspěšných útoků.  
  
## <a name="visual-c-security-features"></a>Zabezpečení funkce Visual C++

 Tyto funkce zabezpečení jsou integrované do kompilátoru Visual C++ a propojovací program:  
  
 [/guard (povolení ochrany toku řízení)](../build/reference/guard-enable-control-flow-guard.md)  
 Způsobí, že kompilátor pro analýzu toku řízení pro cíle nepřímé volání v době kompilace a pak se vložit kód pro ověření cíle za běhu.  
  
 [/GS (kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md)  
 Dává pokyn kompilátoru k vložení do funkce, které mají být zneužity kód pro detekci přetečení. Při zjištění překročení zastavením spuštění. Ve výchozím nastavení tato možnost zapnutá.  
  
 [/SAFESEH (image má bezpečné obslužné rutiny výjimek)](../build/reference/safeseh-image-has-safe-exception-handlers.md)  
 Přikáže linkeru, aby do výstupní image zahrnout tabulku, která obsahuje adresu každé obslužné rutiny výjimky. V době běhu operační systém používá tuto tabulku abyste měli jistotu, že jsou provedeny obslužné rutiny výjimek pouze legitimní. To pomáhá zabránit spuštění obslužné rutiny výjimek, které vznikají zavlečením napadením se zlými úmysly v době běhu. Tento parametr je standardně vypnutý.  
  
 [/ NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (kompatibilní s předcházením spuštění dat)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)  
 Tyto kompilátoru a možnosti linkeru zajištění kompatibility Zabránění spuštění dat (DEP). Zabránění spuštění dat chrání procesoru pro provádění bez znakové stránky.  
  
 [/analyze (analýza kódu)](../build/reference/analyze-code-analysis.md)  
 Tato možnost kompilátoru aktivuje analýzy kódu, který bude hlásit potenciální problémy se zabezpečením, jako je například přetečení vyrovnávací paměti, neinicializovaná paměť, přístup přes ukazatel s hodnotou null a nevracení paměti. Tento parametr je standardně vypnutý. Další informace najdete v tématu [analýzy kódu pro C/C++ přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
 [/DYNAMICBASE (použití modulu pro náhodné rozložení adresního prostoru)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)  
 Tohoto parametru linkeru umožňuje vytváření spustitelnou bitovou kopii, která je možné načíst na různých místech v paměti na začátku spuštění. Tato možnost také umožňuje umístění zásobníku v paměti méně předvídatelné.  
  
## <a name="security-enhanced-crt"></a>Rozšířené zabezpečení CRT  
 Knihovna Runtime jazyka C (CRT) má rozšířený zahrnout bezpečné verze funkcí, které představují riziko zabezpečení – třeba Nekontrolovaná `strcpy` řetězec funkce kopírování. Protože starší, nezabezpečené verze těchto funkcí jsou zastaralé, způsobují upozornění kompilace. Doporučujeme vám použít bezpečné verze těchto funkcí CRT místo potlačení upozornění kompilace. Další informace najdete v tématu [funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="safeint-library"></a>SafeInt – knihovna  
 [SafeInt – knihovna](../windows/safeint-library.md) pomáhá zabránit přetečení celého čísla a jiné zneužitelné chyby, které mohou nastat při používání matematických operací. `SafeInt` Knihovna obsahuje [SafeInt – třída](../windows/safeint-class.md), [SafeIntException – třída](../windows/safeintexception-class.md)a několik [SafeInt – funkce](../windows/safeint-functions.md).  
  
 `SafeInt` Třídy chrání proti přetečení celého čísla a zneužije dělení nulou. Slouží ke zpracování porovnání hodnoty různých typů. Poskytuje dvě zásady zpracování chyb. Výchozí zásada je určená pro `SafeInt` třídy na výjimku `SafeIntException` třídy výjimky do sestavy, proč matematické operaci nejde dokončit. Druhá zásada je určená pro `SafeInt` třídy k zastavení vykonávání programu. Můžete také definovat vlastní zásady.  
  
 Každý `SafeInt` funkce chrání jeden matematické operace z zneužitelné chyby. Bez převodu na stejný typ, můžete použít dva různé typy parametrů. Chcete-li chránit více matematické operace, použijte `SafeInt` třídy.  
  
## <a name="checked-iterators"></a>Checked – iterátory  
 Kontrolovaný iterátor vynucuje hranice kontejneru. Ve výchozím nastavení když kontrolovaného iterátoru je mimo rozsah, generuje výjimku a ukončí provádění programu. Kontrolovaný iterátor poskytuje další úrovně odpovědi, které závisí na hodnotách, které jsou přiřazeny k preprocesoru, jako  **\_SECURE\_SCL\_VYVOLÁ** a  **\_ITERÁTORU\_ladění\_úroveň**. Například na  **\_ITERÁTORU\_ladění\_LEVEL = 2**, kontrolovaného iterátoru poskytuje komplexní kontroly správnosti v režimu ladění, které jsou k dispozici pomocí kontrolních příkazů. Další informace najdete v tématu [Checked Iterators](../standard-library/checked-iterators.md) a [ \_ITERÁTORU\_ladění\_úroveň](../standard-library/iterator-debug-level.md).  
  
## <a name="code-analysis-for-managed-code"></a>Analýza kódu pro spravovaný kód  
 Analýza kódu pro spravovaný kód, označované také jako FxCop, zkontroluje sestavení pro soulad s pokyny k návrhu rozhraní.NET Framework. FxCop analyzuje kódu a metadata v každé sestavení ke kontrole chyb v těchto oblastech:  
  
-   Knihovna návrhu  
  
-   Lokalizace  
  
-   Zásady vytváření názvů  
  
-   Výkon  
  
-   Zabezpečení  
  
## <a name="windows-application-verifier"></a>Ověřovatel aplikací Windows  
 Ověřovatel aplikací (nástroj AppVerifier) pomáhá identifikovat možné problémy kompatibility, stabilitu a zabezpečení aplikace.  
  
 Nástroj AppVerifier sleduje, jak aplikace používá operační systém. Sleduje systém souborů, registry, paměť a rozhraní API, zatímco aplikace běží a doporučuje zdrojový kód opravy problémů, které nalezl.  
  
 Můžete použít nástroj AppVerifier na:  
  
-   Test pro potenciální chyby kompatibility aplikace, které jsou způsobeny běžné programovací chyby.  
  
-   Prozkoumejte aplikace pro problémy související s pamětí.  

-   Identifikujte potenciální problémy se zabezpečením v aplikaci.  
  
 Nástroj AppVerifier je součástí sady Application Compatibility Toolkit, který je k dispozici [kompatibilita aplikací](http://go.microsoft.com/fwlink/p/?linkid=91277) na webu TechNet.  
  

## <a name="windows-user-accounts"></a>Uživatelské účty Windows  
 Pomocí Windows uživatelské účty, které patří zpřístupňuje vývojářům skupiny Administrators a--rozšířením – zákazníkům bezpečnostní rizika. Další informace najdete v tématu [spuštění jako člen skupiny Users](running-as-a-member-of-the-users-group.md) a [jak řízení uživatelských účtů (UAC) ovlivňuje vaše aplikace](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Pokyny pro kanály na straně spekulativního spouštění

Informace o tom, k identifikaci a zmírnění zranitelná spekulativního spouštění na straně kanálu hardware v C++ softwaru najdete v tématu [C++ informace pro vývojáře pro kanály na straně provádění spekulativní](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Viz také  
<xref:System.Security>   
[Zabezpečení](/dotnet/standard/security/index)   
[Jak nástroj Řízení uživatelských účtů (UAC) ovlivňuje vaši aplikaci](how-user-account-control-uac-affects-your-application.md)