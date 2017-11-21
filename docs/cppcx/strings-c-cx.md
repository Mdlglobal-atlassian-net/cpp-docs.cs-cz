---
title: "Řetězce (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
caps.latest.revision: "22"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 20b2cf3ac565bfd6bbda39825e55e4171781c737
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strings-ccx"></a>Řetězce (C + +/ CX)
Představuje text v prostředí Windows Runtime v jazyce C + +/ CX pomocí [Platform::String třída](../cppcx/platform-string-class.md). Použití `Platform::String Class` při předání řetězce a zpět do metod v prostředí Windows Runtime třídy, nebo jsou při interakci s ostatními součástmi prostředí Windows Runtime přes hranice binární rozhraní (ABI) aplikace. `Platform::String Class` Poskytuje metody pro několik běžných operací řetězec, ale jeho není navržené jako třídu plné řetězec. V modulu C++, použijte standardní řetězec typy C++ [wstring](../standard-library/basic-string-class.md) žádné významné text zpracování, a pak převést konečné vést ke [Platform::String ^](../cppcx/platform-string-class.md) předtím, než ji předáte do nebo z veřejné rozhraní. Je snadno a efektivně pro převod mezi `wstring` nebo `wchar_t*` a `Platform::String`.  
  
 **Rychlé průchodu**  
  
 V některých případech můžete kompilátor ověřit, že bezpečně můžete vytvořit `Platform::String` nebo předejte `String` funkce bez kopírování v základních datech řetězce. Tyto operace jsou známé jako *rychlé průchodu* a k nim dojde transparentně.  
  
## <a name="string-construction"></a>Vytváření řetězce  
 Hodnota `String` objekt se nedá změnit pořadí (jen pro čtení) z `char16` (16bitové Unicode) znaků. Protože `String` objekt se nedá změnit, přiřazení nové řetězcový literál `String` proměnné ve skutečnosti nahradí původní `String` objekt s novou `String` objektu. Operace sřetězení zahrnují zničení původního `String` objekt a vytvoření nového objektu.  
  
 **Literály**  
  
 A *literálu znak* je znak, který je uzavřena do jednoduchých uvozovek a *řetězcového literálu* je posloupnost znaků, která je uzavřena v uvozovkách. Používáte-li k chybě při inicializaci řetězcový literál ^ proměnné, kompilátor předpokládá, že je literál se skládá z `char16` znaků. To znamená, nemusíte uveďte před literál s modifikátorem řetězec "L" nebo zadejte literál v **_T()** nebo **TEXT()** makro. Další informace o podpoře C++ pro kódování Unicode najdete v tématu [souhrn programování Unicode](../text/unicode-programming-summary.md).  
  
 Následující příklad ukazuje různé způsoby, jak vytvořit `String` objekty.  
  
 [!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]  
  
## <a name="string-handling-operations"></a>Zpracování operace řetězců  
 `String` Třída poskytuje metody a operátory pro zřetězení, porovnání řetězců a další základní operace s řetězci. Pokud chcete provést rozsáhlejší manipulace s řetězci, použijte `String::Data()` – členská funkce načíst hodnotu `String^` objekt jako `const wchar_t*`. Potom tuto hodnotu použít k chybě při inicializaci `std::wstring`, která nabízí bohaté řetězec funkce pro zpracování.  
  
 [!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]  
  
## <a name="string-conversions"></a>Převod řetězců  
 A `Platform::String` může obsahovat pouze `char16` znaky, nebo `NULL` znak. Pokud má vaše aplikace pro práci s 8 rozšířené znaky, použijte [String::Data](../cppcx/platform-string-class.md#data) extrahovat text jako `const wchar_t*`. Pak můžete použít vhodné funkce systému Windows nebo funkce standardní knihovny pro provoz na datech a převést jej zpět na `wchar_t*` nebo [wstring](../standard-library/basic-string-class.md), který můžete použít k vytvoření nové `Platform::String`.  
  
 Následující fragment kódu ukazuje, jak převést `String^` do a z proměnné `wstring` proměnné. Další informace o zacházení s řetězci, který se používá v tomto příkladu najdete v tématu [basic_string::replace](../standard-library/basic-string-class.md#replace).  
  
 [!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]  
  
## <a name="string-length-and-embedded-null-values"></a>Délka řetězce a vložené hodnoty NULL  
 [String::Length](../cppcx/platform-string-class.md#length) vrátí počet znaků v řetězci, nikoli počet bajtů. Ukončovací znak hodnoty NULL není považována, pokud je explicitně zadat ho použijete-li vytvořit řetězec sémantika zásobníku.  
  
 A `Platform::String` může obsahovat vložené hodnoty NULL, ale jenom v případě, že je výsledek operace zřetězení hodnotu NULL. Vložené hodnoty Null nejsou podporovány v textové literály; proto nelze použít embedded hodnoty Null v tomto režimu k chybě při inicializaci `Platform::String`. Vložené hodnoty NULL v `Platform::String` jsou při řetězec se zobrazí, například když jsou přiřazeny ke ignorováno `TextBlock::Text` vlastnost. Vložené hodnoty Null se odeberou, když je hodnota řetězce vrácené `Data` vlastnost.  
  
## <a name="stringreference"></a>StringReference  
 V některých případech kódu (a) přijímá std::wstring nebo wchar_t řetězec nebo L"" řetězec literálu, jenom předává je na jinou metodu, která přebírá řetězec ^ jako vstupní parametr. Dokud původní řetězec vyrovnávací paměť samotného zůstává platná a není mutovat, než se vrátí funkce, můžete převést `wchar_t*` řetězec nebo řetězcový literál [Platform::StringReference](../cppcx/platform-stringreference-class.md)a předejte v tom, že místo `Platform::String^`. To je povoleno, protože `StringReference` má uživatelem definovaný převod na `Platform::String^`. Pomocí `StringReference` vyvarujte zvláštní kopii dat řetězce. V smyčky, kde jsou předávání velké počty řetězce nebo při předávání velké řetězce, můžete případně dosáhnout zlepšení výkonu pomocí `StringReference`. Ale protože `StringReference` v podstatě vypůjčí původní řetězec vyrovnávací paměť, je nutné použít mimořádně pečlivě vyhnete se tak poškození paměti. Neměli předat `StringReference` pro asynchronní metodu Pokud původního řetězce záruku, že se v oboru, když tato metoda vrátí. Řetězec ^ který je inicializován ze StringReference vynutí přidělení a kopírování řetězcových dat. Pokud dojde k druhá operace přiřazení. V takovém případě dojde ke ztrátě výkonu výhodou `StringReference`.  
  
 Všimněte si, že `StringReference` je standardní C++ – třída typu, ne ref třídu, nelze ji použít v veřejné rozhraní ref tříd, které definujete.  
  
 Následující příklad ukazuje, jak používat StringReference:  
  
```  
void GetDecodedStrings(std::vector<std::wstring> strings)  
{  
    using namespace Windows::Security::Cryptography;  
    using namespace Windows::Storage::Streams;  
  
    for (auto&& s : strings)  
    {  
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)  
        // Call using StringReference:  
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));  
  
        //...do something with buffer  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Vestavěné typy](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f)