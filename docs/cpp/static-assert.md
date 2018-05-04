---
title: static_assert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_assert_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47046090da45d963cc0005f47e2bea680ad17795
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="staticassert"></a>static_assert
Testuje softwarové tvrzení v době kompilace. Pokud je zadaný konstantní výraz `false`, kompilátor zobrazí určenou zprávu, pokud je k dispozici a kompilace se nezdaří s chybou C2338; jinak deklaraci nemá žádný vliv.  
  
## <a name="syntax"></a>Syntaxe  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`constant-expression`|Celočíselné konstantní výraz, který lze převést na logickou hodnotu.<br /><br /> Je-li vyhodnocený výraz nula (false), `string-literal` parametr se zobrazí a kompilace se nezdaří s chybou. Pokud ve výrazu je nenulové hodnoty (pravda), `static_assert` deklarace nemá žádný vliv.|  
|`string-literal`|Zprávu, která se zobrazí, pokud `constant-expression` parametr je nulová. Zpráva je řetězec znaků [základní znakovou sadu](../c-language/ascii-character-set.md) kompilátoru; je, nikoli [vícebajtové a široké znaky](../c-language/multibyte-and-wide-characters.md).|  
  
## <a name="remarks"></a>Poznámky  
 `constant-expression` Parametr `static_assert` představuje deklarace *softwaru assertion*. Kontrolní výraz softwaru Určuje podmínku, která byste měli být na určitém místě v programu na hodnotu true. Pokud je podmínka vyhodnocena jako true, `static_assert` deklarace nemá žádný vliv. Pokud je podmínka vyhodnocena jako false, kontrolní výraz selže, kompilátor zobrazí zprávu ve `string-literal` parametr a kompilace selže s chybou. Visual Studio 2017 a novější je volitelný parametr řetězcový literál. 
  
 `static_assert` Deklarace testuje softwarové tvrzení v době kompilace. Naproti tomu [assert – makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro testuje assertion softwaru v době běhu a vznikly náklady běhu v místa a času. `static_assert` Deklarace je zvláště užitečná pro ladění šablony, protože můžou být součástí šablony argumenty `constant-expression` parametr.  
  
 Kompilátor prověří `static_assert` deklarace chyby syntaxe, když dojde k deklaraci. Kompilátor vyhodnotí `constant-expression` parametr okamžitě, pokud není závislý na parametru šablony. Jinak, kompilátor vyhodnotí `constant-expression` parametr při vytváření instance šablony. V důsledku toho kompilátor může vydat diagnostické zprávy jednou při zjistil deklaraci se a znovu když šablona je vytvořena instance.  
  
 Můžete použít `static_assert` – klíčové slovo v oboru názvů, třída nebo obor bloku. ( `static_assert` – Klíčové slovo je technicky deklaraci, i když ho nezavádí nový název do programu, protože je možné použít v oboru názvů.)  
  
## <a name="description"></a>Popis  
 V následujícím příkladu `static_assert` deklarace má obor názvů. Protože kompilátor zná velikost typu `void *`, je tento výraz vyhodnocen okamžitě.  
  
## <a name="example"></a>Příklad  
  
```  
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>Popis  
 V následujícím příkladu `static_assert` deklarace má rozsah třídy. `static_assert` Ověřuje, že je parametr šablony *prostý stará data* typu (POD). Kompilátor prověří `static_assert` deklarace je deklarovaná, ale nelze vyhodnotit `constant-expression` parametr až `basic_string` vytvoření instance šablony třídy v `main()`.  
  
## <a name="example"></a>Příklad  
  
```  
#include <type_traits>  
#include <iosfwd>  
namespace std {  
template <class CharT, class Traits = std::char_traits<CharT> >  
class basic_string {  
    static_assert(std::is_pod<CharT>::value,  
                  "Template argument CharT must be a POD type in class template basic_string");  
    // ...  
    };  
}  
  
struct NonPOD {  
    NonPOD(const NonPOD &) {}  
    virtual ~NonPOD() {}  
};  
  
int main()  
{  
    std::basic_string<char> bs;  
}  
```  
  
## <a name="description"></a>Popis  
 V následujícím příkladu `static_assert` deklarace obsahuje rozsah bloku. `static_assert` Ověřuje, že velikost strukturu VMPage je rovno pagesize virtuální paměti systému.  
  
## <a name="example"></a>Příklad  
  
```  
#include <sys/param.h> // defines PAGESIZE  
class VMMClient {  
public:  
    struct VMPage { // ...   
           };  
    int check_pagesize() {  
    static_assert(sizeof(VMPage) == PAGESIZE,  
        "Struct VMPage must be the same size as a system virtual memory page.");  
    // ...  
    }  
// ...  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Kontrolní výraz a uživatelem zadané zprávy (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [#error – direktiva (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [Šablony](../cpp/templates-cpp.md)   
 [Znaková sada ASCII](../c-language/ascii-character-set.md)   
 [Deklarace a definice](declarations-and-definitions-cpp.md)