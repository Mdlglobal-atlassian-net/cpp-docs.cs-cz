---
title: Chyby a výjimky zpracování (moderní verze jazyka C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94a9e75770e822c89ea65a745a2fca491f175d95
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569859"
---
# <a name="errors-and-exception-handling-modern-c"></a>Ošetření chyb a výjimek (moderní verze jazyka C++)
V moderní verze jazyka C++, ve většině scénářů je upřednostňovaný způsob, jak sestav a zpracování logiky chyby a chyby za běhu použít výjimky. To platí hlavně při zásobníku může obsahovat několik volání funkce mezi funkce, která zjistí chybu a funkce, která má kontext, který má vědět, jak se nezdařilo. Výjimky poskytují způsob formální, dobře definované pro kód, který zjistí chyby k předání informací o zásobníkem volání.  
  
 Program chyby jsou obvykle rozdělit do dvou kategorií: logické chyby, které jsou způsobeny programování zaměnit, například chybu "index je mimo rozsah" a chyby za běhu, které jsou mimo kontrolu programátory, například "není k dispozici síťové služby" došlo k chybě. Ve stylu jazyka C programování a v modelu COM zasílání zpráv o chybách je spravovat a vrátila hodnotu, která představuje kód chyby nebo stavový kód pro konkrétní funkce nebo nastavením globální proměnné, která má volající může volitelně načíst po každé volání funkce v tématu zda byly hlášené chyby. Například programování COM používá ke komunikaci chyby volajícímu návratová hodnota HRESULT a rozhraní API Win32 má funkce GetLastError načíst poslední chybu, která byla hlášena zásobníku volání. V obou případech je to na volající rozpoznat kód a reagovat na ji odpovídajícím způsobem. Pokud má volající není explicitně zpracovat kód chyby, program může dojít k chybě bez upozornění nebo pokračovat ke spouštění s chybná data a vytvářet nesprávné výsledky.  
  
 Výjimky jsou preferované v moderní verze jazyka C++ z následujících důvodů:  
  
-   Výjimka vynutí volajícího kódu rozpoznat chybový stav a zpracovat je. Nezpracované výjimky zastavit spuštění programu.  
  
-   Výjimku přejde do bodu v zásobníku volání, který může zpracovat chyba. Zprostředkující funkce nechat výjimka rozšířit. Pro koordinaci s vrstvami, nemají.  
  
-   Mechanismus uvolnění zásobníku výjimek zničí všechny objekty v oboru podle dobře definovaných pravidel po je vyvolána výjimka.  
  
-   Výjimku umožňuje čistou oddělení mezi kód, který zjistí chybu a kód, který zpracovává chyby.  
  
 Následující příklad zjednodušené ukazuje nezbytné syntaxe pro vyvolání a zachytávání výjimek v jazyce C++.  
  
```cpp  
#include <stdexcept>  
#include <limits>  
#include <iostream>  
  
using namespace std;  
class MyClass  
{  
public:  
   void MyFunc(char c)  
   {  
      if(c > numeric_limits<char>::max())  
         throw invalid_argument("MyFunc argument too large.");  
      //...  
   }  
};  
  
int main()  
{  
   try  
   {  
      MyFunc(256); //cause an exception to throw  
   }  
  
   catch(invalid_argument& e)  
   {  
      cerr << e.what() << endl;  
      return -1;  
   }  
   //...  
   return 0;  
}  
  
```  
  
 Výjimek v jazyce C++ je podobných v jazyků, například C# nebo Java. V `try` blokování, pokud je výjimku *vyvolána* bude *zachycena* prvním přidružené `catch` bloku, jejíž typ se shoduje s výjimky. Jinými slovy, provádění přejde z `throw` příkaz, který má `catch` příkaz. Pokud se nenajde žádný blok catch použitelný, `std::terminate` je volána a program bude ukončen. V jazyce C++ může být vyvolána libovolného typu; Doporučujeme však vyvolávat výjimku typu, který pochází přímo nebo nepřímo z `std::exception`. V předchozím příkladu, typ výjimky [invalid_argument](../standard-library/invalid-argument-class.md), je definována v knihovně standardní ve [ \<stdexcept – >](../standard-library/stdexcept.md) soubor hlaviček. C++ nepodporuje a nevyžaduje, `finally` bloku a ujistěte se, že všechny prostředky jsou uvolněny, pokud je vyvolána výjimka. Získávání prostředků je stylu inicializace (RAII), který používá chytré ukazatele, poskytuje požadované funkce pro vyčištění prostředků. Další informace najdete v tématu [postupy: návrh na bezpečnost výjimek](../cpp/how-to-design-for-exception-safety.md). Informace o mechanismus uvolnění zásobníku C++ najdete v tématu [výjimky a Unwinding zásobníku](../cpp/exceptions-and-stack-unwinding-in-cpp.md).  
  
## <a name="basic-guidelines"></a>Základní pokyny  
 Zpracování chyb robustní je náročné v žádný programovací jazyk. I když výjimky poskytovat několik funkcí, které podporují dobrý zpracování chyb, není všechnu práci za vás. Pokud chcete výhod mechanismus výjimek, mějte výjimky při navrhování kódu.  
  
-   Použití nepodmíněných výrazů ke kontrole chyb, které by nikdy nedojde. Výjimky použijte ke kontrole chyb, ke kterým může dojít například chyb při ověřování vstupních parametrů veřejné funkcí. Další informace najdete v části s názvem **výjimky vs. Kontrolní výrazy**.  
  
-   Výjimky použijte, pokud kód, který zpracovává chyba může být z kód, který zjistí chybu odděleny jeden nebo více použité volání funkcí. Zvážit, zda chcete používat kódy chyb místo v kritické výkonu smyčky, pokud kód, který zpracovává chyba je úzce párované na kód, který zjistí ho. 
  
-   Pro každou funkci, která může vyvolat nebo rozšířit výjimku, zadejte některou z záruky tři výjimka: silné záruky, základní záruka nebo záruka nothrow (noexcept). Další informace najdete v tématu [postupy: návrh na bezpečnost výjimek](../cpp/how-to-design-for-exception-safety.md).  
  
-   Generování výjimek podle hodnoty, je zachytit odkazem. Nemáte catch co nemůže zpracovat. 
  
-   Nepoužívejte specifikace výjimek, které jsou zastaralé v C ++ 11. Další informace najdete v části s názvem **specifikace výjimek a noexcept**.  
  
-   Typy výjimek standardní knihovna použijte, pokud se vztahují. Odvození typů vlastní výjimky z [třída exception](../standard-library/exception-class.md) hierarchie.  
  
-   Nepovolit výjimky vyhnuli z destruktory nebo zrušení přidělení paměti funkce.  
  
## <a name="exceptions-and-performance"></a>Výjimky a výkonu  
 Mechanismus výjimek má velmi minimální výkon, pokud nedojde k výjimce. Pokud je vyvolána výjimka, náklady na řešení traversal zásobníku a unwinding je přibližně porovnatelný z hlediska náklady na volání funkce. Jsou potřeba ke sledování zásobníku volání po další datové struktury `try` zadán bloku a další pokyny jsou nutné k unwind zásobníku, pokud je vyvolána výjimka. Ale ve většině scénářů, náklady na výkon a spotřeba paměti není důležité. Nežádoucí vliv na výkon výjimek je pravděpodobně významné pouze v systémech velmi omezené paměti nebo ve výkonu kritické cyklu kde chybu je pravděpodobně nastane pravidelně a kód pro zpracování ho je úzce párované na kód, který ho sestavy. V každém případě je možné vědět skutečné náklady výjimek bez profilace a měření. I ve vzácných případech náklady je důležité, vám může nejtěžšího ho před vyšší správnost a jednodušší udržovatelnosti a další výhody, které jsou k dispozici zásady dobře navrženou výjimka.  
  
## <a name="exceptions-vs-assertions"></a>Výjimky a kontrolní výrazy  
 Výjimky a vyhodnotí jsou dva odlišné mechanismy pro zjišťování běhové chyby v programu. Použití nepodmíněných výrazů k testování podmínky během vývoje, který by nikdy neměly být hodnota true, pokud jste kód napsali správně. Neexistuje žádný bod při zpracování takové chyby pomocí výjimku, protože Chyba určuje, že něco v kódu má být odstraněna a nepředstavuje podmínku, která má program pro obnovení z za běhu. Assert zastaví provádění na příkaz tak, aby si můžete prohlédnout stav programu v ladicím programu; výjimku pokračuje v provádění z první obslužná rutina odpovídající catch. Pomocí výjimky Zkontrolujte chybové stavy, které můžou nastat v době běhu i v případě, že jste kód napsali správně, například "soubor nebyl nalezen" nebo "nedostatek paměti." Můžete chtít obnovit z těchto podmínek, i v případě obnovení právě výstupy zprávu do protokolu a program se ukončí. Vždy zkontrolujte argumenty pro veřejné funkce pomocí výjimky. I v případě, že funkce je, bez chyb, nemusí mít plnou kontrolu nad argumenty, které může předat uživatele.  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Výjimky jazyka C++ a Windows SEH výjimky  
 Programy C a C++ můžete použít strukturovaného zpracování mechanismus (SEH) v operačním systému Windows výjimek. Koncepty v SEH vypadat podobně jako v výjimky jazyka C++, s tím rozdílem, že používá SEH `__try`, `__except`, a `__finally` vytvoří místo `try` a `catch`. V jazyce Visual C++ jsou pro SEH implementované výjimky jazyka C++. Ale při psaní kódu jazyka C++ pomocí syntaxe výjimky jazyka C++.  
  
 Další informace o SEH najdete v tématu [strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md).  
  
## <a name="exception-specifications-and-noexcept"></a>Specifikace výjimek a noexcept  
 Specifikace výjimek byly zavedeny v jazyce C++ jako způsob, jak určit výjimky, které může vyvolat funkci. Specifikace výjimek však prokázat problematické v praxi a jsou zastaralé ve standardu C ++ 11 konceptu. Doporučujeme, abyste nepoužívejte specifikace výjimek s výjimkou `throw()`, která označuje, že funkce umožňuje žádné výjimky, abyste se vyhnuli. Pokud musíte použít specifikace výjimek typu `throw(` *typ*`)`, uvědomte si, že Visual C++ vyplouvající z standardní určitými způsoby. Další informace najdete v tématu [specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md). `noexcept` Specifikátor byla zavedená v C ++ 11 jako upřednostňovaný alternativa k `throw()`.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: rozhraní mezi kódem výjimek a ostatním kódem](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
