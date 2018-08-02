---
title: static_assert | Dokumentace Microsoftu
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
ms.openlocfilehash: 6fa9b8fb7fe85aca21e90195534f33201bee59fc
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464931"
---
# <a name="staticassert"></a>static_assert
Testuje výraz softwaru v době kompilace. Pokud se zadaný výraz konstanty je FALSE, kompilátor zobrazí zadanou zprávu, pokud je zadáno a kompilace selže s chybou C2338; jinak deklarace nemá žádný vliv.  
  
## <a name="syntax"></a>Syntaxe  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*constant-expression*|Celočíselný konstantní výraz, který lze převést na logickou hodnotu.<br /><br /> Pokud vyhodnocený výraz je nula (false), *řetězcový literál* parametrů se zobrazí a kompilace selže s chybou. Pokud má výraz hodnotu nenulová (pravda), **static_assert** deklarace nemá žádný vliv.|  
|*řetězcový literál*|Zprávu, která se zobrazí, pokud *konstantní výraz* parametru je nula. Zpráva je řetězec znaků [základní znakové sadě](../c-language/ascii-character-set.md) kompilátoru; který je, nikoli [vícebajtové široké znaky](../c-language/multibyte-and-wide-characters.md).|  
  
## <a name="remarks"></a>Poznámky  
 *Konstantní výraz* parametr **static_assert** představuje prohlášení *softwarové tvrzení*. Softwarové tvrzení Určuje podmínku, která očekáváte, že na hodnotu true v určitém místě v programu. Pokud je podmínka pravdivá, **static_assert** deklarace nemá žádný vliv. Pokud je podmínka NEPRAVDA, výraz se nezdaří, kompilátor zobrazí zprávu v *řetězcový literál* parametr a kompilace selže s chybou. V sadě Visual Studio 2017 nebo novější je volitelný parametr řetězcový literál. 
  
 **Static_assert** deklarace testuje výraz softwaru v době kompilace. Naproti tomu [vyhodnocení makra, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) – makro testuje výraz softwaru v době běhu a má náklady běhu prostor nebo čas. **Static_assert** deklarace je zvláště užitečná pro šablony ladění, protože argumenty šablony mohou být součástí *konstantní výraz* parametru.  
  
 Kompilátor ověří **static_assert** prohlášení o syntaktických chybách při výskytu prohlášení. Kompilátor vyhodnotí *konstantní výraz* parametr okamžitě, pokud není závislý na parametru šablony. V opačném případě kompilátor vyhodnocuje *konstantní výraz* parametr při vytváření instance šablony. V důsledku toho kompilátor může vydat diagnostickou zprávu jednou při výskytu prohlášení a znovu když šablona je vytvořena instance.  
  
 Můžete použít **static_assert** – klíčové slovo v oboru názvů, třídy nebo oboru bloku. ( **Static_assert** – klíčové slovo je technicky prohlášení, i když nezavádí nové jméno do programu, protože může být použito v oboru názvů.)  
  
## <a name="description"></a>Popis  
 V následujícím příkladu **static_assert** má deklarace oboru názvů. Protože kompilátor zná velikost typu `void *`, je výraz vyhodnocen ihned.  
  
## <a name="example"></a>Příklad  
  
```cpp 
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>Popis  
 V následujícím příkladu **static_assert** má deklarace oboru třídy. **Static_assert** ověří, zda je parametr šablony *obyčejná stará data* typ (POD). Kompilátor ověří **static_assert** prohlášení, pokud je deklarovaná, ale není vyhodnocen *konstantní výraz* parametr do `basic_string` v vytvářeníinstancešablonytřídy`main()`.  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
 V následujícím příkladu **static_assert** má deklarace oboru bloku. **Static_assert** ověří, zda je velikost struktury VMPage rovna pagesize virtuální paměti systému.  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
## <a name="see-also"></a>Viz také:  
 [Kontrolní výraz a uživatelem zadané zprávy (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [#error – direktiva (C++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [Šablony](../cpp/templates-cpp.md)   
 [Znaková sada ASCII](../c-language/ascii-character-set.md)   
 [Deklarace a definice](declarations-and-definitions-cpp.md)