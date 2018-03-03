---
title: "Převody a bezpečnost typů (moderní verze jazyka C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c77b7269ae70d24878ff02c0661b60365c76d1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-conversions-and-type-safety-modern-c"></a>Převody a bezpečnost typů (moderní verze jazyka C++)
Tento dokument popisuje běžné problémy při převodu typů a také způsob, jak jim zabránit v kódu jazyka C++.  
  
 Při psaní programu jazyka C++ je důležité zajistit, že je typově bezpečný. To znamená, že v každé proměnné, argumentu funkce a návratové hodnotě funkce je uložen přijatelný druh dat a že operace zahrnující hodnoty různých typů mají smysl a nezpůsobují ztrátu dat, nesprávnou interpretaci bitových vzorů nebo poškození paměti. Program je podle definice typově bezpečný, pokud nikdy explicitně ani implicitně nepřevádí hodnoty jednoho typu na jiný typ. Avšak převody typů, a to dokonce nebezpečné převody, jsou někdy nutné. Například výsledek operace s čísly s plovoucí desetinnou čárkou bude nutné uložit do proměnné typu `int` nebo bude nutné předat hodnotu typu `int` bez znaménka funkci, která přebírá typ `int` se znaménkem. Oba příklady představují nebezpečné převody, protože mohou způsobit ztrátu dat nebo neplatnou interpretaci hodnoty.  
  
 Když kompilátor zjistí nebezpečný převod, vyvolá chybu nebo upozornění. Chyba přeruší kompilaci. Upozornění umožní pokračování kompilace a označí možnou chybu v kódu. Nicméně i v případě, že se váš program zkompiluje bez upozornění, může kód stále obsahovat implicitní převody typů poskytující nesprávné výsledky. Chyby typů mohou být rovněž způsobeny explicitními převody nebo přetypováním v kódu.  
  
## <a name="implicit-type-conversions"></a>Implicitní převody typu  
 Pokud některý výraz obsahuje operandy různých předdefinovaných typů a jsou k dispozici žádné explicitní přetypování, kompilátor použije integrované *standardní převody* pro převod jedné z operandy tak, aby odpovídaly typy. Kompilátor se pokusí provést převod v přesně určeném pořadí, dokud některý krok neuspěje. Pokud je vybraným převodem povýšení, kompilátor upozornění nevyvolá. Je-li převod zužující, kompilátor vyvolá upozornění na možnou ztrátu dat. To, zda skutečně dojde ke ztrátě dat, závisí na skutečných zúčastněných hodnotách, avšak doporučujeme považovat toto upozornění za chybu. Pokud se jedná o uživatelský typ, kompilátor se pokusí provést převody zadané v definici této třídy. Pokud kompilátor nenajde přijatelný převod, vyvolá chybu a program nezkompiluje. Další informace o pravidlech, která řídí standardní převody najdete v tématu [standardní převody](../cpp/standard-conversions.md). Další informace o uživatelem definovaných převodů najdete v tématu [uživatelem definovaných převodů (C + +/ CLI)](../dotnet/user-defined-conversions-cpp-cli.md).  
  
### <a name="widening-conversions-promotion"></a>Rozšiřující převody (povýšení)  
 U rozšiřujícího převodu je hodnota menší proměnné přiřazena větší proměnné bez ztráty dat. Protože rozšiřující převody jsou vždy bezpečné, kompilátor je provede bez vyvolání upozornění. Následující převody jsou rozšiřující převody.  
  
|From|Chcete-li|  
|----------|--------|  
|Jakýkoli celočíselný typ se znaménkem nebo bez znaménka s výjimkou typů `long long` a `__int64`|`double`|  
|`bool`nebo`char`|Jakýkoli jiný předdefinovaný typ|  
|`short`nebo`wchar_t`|`int`, `long`, `long long`|  
|`int`, `long`|`long long`|  
|`float`|`double`|  
  
### <a name="narrowing-conversions-coercion"></a>Zužující převody  
 Zužující převody kompilátor provádí implicitně, upozorní však na možnou ztrátu dat. Tato upozornění berte velmi vážně. Pokud jste si jisti, že nedojde ke ztrátě dat, protože hodnoty ve větší proměnné se vždy vejdou do menší proměnné, přidejte explicitní přetypování, aby kompilátor přestal vyvolávat tato upozornění. Pokud si nejste jisti, zda jde o bezpečný převod, přidejte do kódu nějaký druh kontroly za běhu programu, abyste zjistili možnou ztrátu dat, která by mohla způsobit nesprávné výsledky programu. 
  
 Jakýkoli převod typu s plovoucí desetinnou čárkou na celočíselný typ je zužující převod, protože necelá část hodnoty s plovoucí desetinnou čárkou je zahozena a ztracena.  
  
 Následující příklad kódu ukazuje některé implicitní zužující převody a upozornění, která pro ně kompilátor vyvolá.  
  
```cpp  
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow  
wchar_t wch = 'A'; //OK  
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'  
              // to 'char', possible loss of data  
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from  
                           // 'int' to 'unsigned char'  
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to  
              // 'int', possible loss of data  
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to  
             // 'int', possible loss of data  
```  
  
### <a name="signed---unsigned-conversions"></a>Převody hodnot se znaménkem a bez znaménka  
 Celočíselný typ se znaménkem a jeho protějšek bez znaménka mají vždy stejnou velikost, ale liší se interpretací bitového vzoru transformace hodnoty. Následující příklad kódu demonstruje, co se stane, když je stejný bitový vzor interpretován jako hodnota se znaménkem a jako hodnota bez znaménka. Bitový vzor uložený v proměnných `num` a `num2` zůstane vždy stejný, jak je zobrazeno v předchozí ilustraci.  
  
```cpp  
using namespace std;  
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>  
short num2 = num;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
// Go the other way.  
num2 = -1;  
num = num2;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
```  
  
 Všimněte si, že hodnoty jsou interpretovány v obou směrech. Pokud váš program produkuje nesprávné výsledky, ve kterých se zdá být znaménko hodnoty obrácené, než jste očekávali, použijte implicitní převody mezi celočíselnými typy se znaménkem a bez znaménka. V následujícím příkladu, výsledkem výrazu (0 - 1) je implicitně převést z `int` k `unsigned int` při uložení v `num`. To způsobí opětovnou interpretaci bitového vzoru.  
  
```cpp  
unsigned int u3 = 0 - 1;  
cout << u3 << endl; // prints 4294967295  
  
```  
  
 Kompilátor nevyvolá upozornění o implicitních převodech mezi celočíselnými typy se znaménkem a bez znaménka. Proto doporučujeme, abyste se převodům mezi hodnotami se znaménkem a bez znaménka zcela vyhnuli. Pokud jim nelze zabránit, přidejte do kódu kontrolu za běhu programu, abyste zjistili, zda je převáděná hodnota větší než nebo rovna nule a menší než nebo rovna maximální hodnotě typu se znaménkem. Hodnoty v tomto rozsahu budou převedeny z hodnoty se znaménkem na hodnotu bez znaménka nebo z hodnoty bez znaménka na hodnotu se znaménkem bez opětovné interpretace.  
  
### <a name="pointer-conversions"></a>Převody ukazatele  
 V mnoha výrazech je pole stylu jazyka C implicitně převedeno na ukazatel na první element v tomto poli a ke konstantním převodům může dojít bez upozornění. I když je to pohodlné, je to také potenciálně náchylné k chybám. Například následující ukázka špatně navrženého kódu se zdá být nesmyslná, ale v jazyce Visual C++ bude zkompilována a jako výsledek vrátí znak 'p'. Nejprve je konstantní textový literál „Help“ převeden na typ `char*` odkazující na první prvek pole. Tento ukazatel je poté zvýšen o tři prvky, takže nyní odkazuje na poslední prvek 'p'.  
  
```cpp  
char* s = "Help" + 3;  
  
```  
  
## <a name="explicit-conversions-casts"></a>Explicitní převody (přetypování)  
 Pomocí operace přetypování lze kompilátoru dát pokyn k převodu hodnoty z jednoho typu na jiný typ. Kompilátor vyvolá chybu v případech, kdy jsou dva typy naprosto nesouvisející, ale v jiných případech chybu nevyvolá, i když operace není typově bezpečná. Přetypování používejte opatrně, protože jakýkoli převod jednoho typu na jiný je možným zdrojem chyby programu. Použití přetypování je však někdy nutné a ne každé je stejně bezpečné. Efektivně lze přetypování využít, pokud váš kód provádí zužující převod a víte, že tento převod nebude příčinou nesprávných výsledků programu. Ve skutečnosti to kompilátoru říká, že víte, co děláte a přestane vás o tom varovat. Další možností použití je přetypování ukazatele na odvozenou třídu na ukazatele na základní třídu. Další možností použití přetypování je převedení proměnné deklarované jako `const` na proměnnou deklarovanou bez tohoto klíčového slova, což tuto proměnnou umožní předat funkci, která vyžaduje argument deklarovaný bez klíčového slova `const`. Většina těchto operací přetypování představuje určité riziko.  
  
 V programování ve stylu jazyka C se pro všechny druhy přetypování používá stejný operátor přetypování ve stylu jazyka C.  
  
```cpp  
(int) x; // old-style cast, old-style syntax  
int(x); // old-style cast, functional syntax  
  
```  
  
 Operátor přetypování ve stylu jazyka C je stejný jako operátor volání (), je proto v kódu nevýrazný a lze jej snadno přehlédnout. Obojí je špatné, protože je na první pohled nelze jednoduše rozpoznat nebo vyhledat a jsou tak nesourodé, že mohou vyvolat libovolnou kombinaci klíčových slov `static`, `const` a `reinterpret_cast`. Zjištění skutečného významu přetypování ve starém stylu může být obtížné a náchylné k chybám. Z těchto důvodů, pokud je přetypování nutné, doporučujeme použít jeden z následujících operátorů přetypování jazyka C++, které jsou v některých případech významně více typově bezpečné a zřetelněji vyjádří záměr programu:  
  
-   `static_cast` pro přetypování, která jsou kontrolována pouze v době kompilace. Operátor `static_cast` vrátí chybu, pokud kompilátor zjistí, že se pokoušíte o převod mezi typy, které jsou zcela nekompatibilní. Lze jej také použít k převodu mezi ukazatelem na základní třídu a ukazatelem na odvozenou třídu. Kompilátor však nemůže vždy jasně určit, zda tyto převody budou bezpečné i v době běhu.  
  
    ```cpp  
    double d = 1.58947;  
    int i = d;  // warning C4244 possible loss of data  
    int j = static_cast<int>(d);       // No warning.  
    string s = static_cast<string>(d); // Error C2440:cannot convert from  
                                       // double to std:string  
  
    // No error but not necessarily safe.  
    Base* b = new Base();  
    Derived* d2 = static_cast<Derived*>(b);  
  
    ```  
  
     Další informace najdete v tématu [static_cast](../cpp/static-cast-operator.md).  
  
-   `dynamic_cast` pro bezpečné přetypování mezi ukazatelem na základní třídu a ukazatelem na odvozenou třídu kontrolované za běhu. Operátor `dynamic_cast` je v tomto případě bezpečnější než operátor `static_cast`, ačkoli tato kontrola modulu runtime znamená zvýšenou režii.  
  
    ```cpp  
    Base* b = new Base();  
  
    // Run-time check to determine whether b is actually a Derived*  
    Derived* d3 = dynamic_cast<Derived*>(b);  
  
    // If b was originally a Derived*, then d3 is a valid pointer.  
    if(d3)  
    {  
       // Safe to call Derived method.  
       cout << d3->DoSomethingMore() << endl;  
    }  
    else  
    {  
       // Run-time check failed.  
       cout << "d3 is null" << endl;  
    }  
  
    //Output: d3 is null;  
  
    ```  
  
     Další informace najdete v tématu [dynamic_cast](../cpp/dynamic-cast-operator.md).  
  
-   `const_cast` pro přetypování proměnné deklarované jako `const` na proměnnou deklarovanou bez tohoto klíčového slova nebo převod proměnné deklarované bez klíčového slova `const` na proměnnou deklarovanou jako `const`. Přetypování proměnné deklarované jako `const` na nekonstantní proměnnou je stejně náchylné k chybám jako přetypování ve stylu jazyka C s tím rozdílem, že při použití operátoru `const-cast` je mylné provedení přetypování méně pravděpodobné. Někdy je proměnnou deklarovanou jako `const` nutné přetypovat na nekonstantní proměnnou, například při předání proměnné deklarované jako `const` funkci, která vyžaduje parametr deklarovaný bez klíčového slova `const`. Následující příklad ukazuje, jak to provést.  
  
    ```cpp  
    void Func(double& d) { ... }  
    void ConstCast()  
    {  
       const double pi = 3.14;  
       Func(const_cast<double&>(pi)); //No error.  
    }  
  
    ```  
  
     Další informace najdete v tématu [const_cast –](../cpp/const-cast-operator.md).  
  
-   `reinterpret_cast` pro přetypování mezi nesouvisejícími typy, jako je převod typu `pointer` na typ `int`.  
  
    > [!NOTE]
    >  Tento operátor přetypování se nepoužívá tak často jako ostatní a není zaručena jeho přenositelnost na jiné kompilátory.  
  
     Následující příklad ukazuje, jak se operátor `reinterpret_cast` liší od operátoru `static_cast`.  
  
    ```cpp  
    const char* str = "hello";  
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot  
                                  // convert from 'const char *' to 'int'  
    int j = (int)str; // C-style cast. Did the programmer really intend  
                      // to do this?  
    int k = reinterpret_cast<int>(str);// Programming intent is clear.  
                                       // However, it is not 64-bit safe.  
  
    ```  
  
     Další informace najdete v tématu [reinterpret_cast – operátor](../cpp/reinterpret-cast-operator.md).  
  
## <a name="see-also"></a>Viz také  
 [C++ – systém typů](../cpp/cpp-type-system-modern-cpp.md)   
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)