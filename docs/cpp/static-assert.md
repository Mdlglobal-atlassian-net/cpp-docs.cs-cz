---
title: static_assert
ms.date: 07/29/2019
f1_keywords:
- static_assert_cpp
helpviewer_keywords:
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
ms.openlocfilehash: a3336e9e41e3dc6804c2398d3ef815ba8c471e50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160902"
---
# <a name="static_assert"></a>static_assert

Testuje kontrolní výraz softwaru v době kompilace. Pokud je zadaný konstantní výraz FALSE, kompilátor zobrazí zadanou zprávu, pokud je k dispozici, a kompilace se nezdařila s chybou C2338; jinak deklarace nemá žádný vliv.

## <a name="syntax"></a>Syntaxe

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // C++17 (Visual Studio 2017 and later)
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*konstantní výraz*|Celočíselný konstantní výraz, který lze převést na logickou hodnotu.<br /><br /> Pokud je vyhodnocený výraz nula (false), je zobrazen parametr *řetězcového literálu* a kompilace se nezdařila s chybou. Pokud je výraz nenulový (true), deklarace **static_assert** nemá žádný vliv.|
|*řetězcový literál*|Zpráva, která se zobrazí, pokud je parametr *konstantního výrazu* nula. Zpráva je řetězec znaků v [základní znakové sadě](../c-language/ascii-character-set.md) kompilátoru. To znamená, že se nejedná o [vícebajtové nebo velké znaky](../c-language/multibyte-and-wide-characters.md).|

## <a name="remarks"></a>Poznámky

Parametr *konstantního výrazu* **static_assert** deklarace představuje *softwarový kontrolní výraz*. Softwarový kontrolní výraz určuje podmínku, kterou očekáváte, že bude platit v určitém místě v programu. Pokud je podmínka pravdivá, deklarace **static_assert** nemá žádný vliv. Pokud je podmínka false, kontrolní výraz se nezdařil, kompilátor zobrazí zprávu v parametru *String-Literal* a kompilace se nezdařila s chybou. V aplikaci Visual Studio 2017 a novější parametr řetězcového literálu je nepovinný.

Deklarace **static_assert** testuje kontrolní výraz softwaru v době kompilace. Naproti tomu [makro ASSERT a funkce _ASSERT a _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) testovat kontrolní výraz softwaru za běhu a účtují náklady na spuštění v prostoru nebo čase. Deklarace **static_assert** je zvláště užitečná pro šablony ladění, protože argumenty šablony mohou být zahrnuty v parametru *constant-expression* .

Kompilátor prověřuje deklaraci **static_assert** pro chyby syntaxe při zjištění deklarace. Kompilátor vyhodnocuje parametr *konstantního výrazu* okamžitě, pokud není závislý na parametru šablony. V opačném případě kompilátor vyhodnocuje parametr *konstantního výrazu* při vytváření instance šablony. V důsledku toho může kompilátor vystavit diagnostickou zprávu jednou při zjištění deklarace a znovu při vytvoření instance šablony.

Můžete použít klíčové slovo **static_assert** v oboru názvů, třídě nebo rozsahu bloku. (Klíčové slovo **static_assert** je technicky deklarace, i když do programu nezavádí nový název, protože je možné ho použít v oboru názvů.)

## <a name="description"></a>Popis

V následujícím příkladu má deklarace **static_assert** obor názvů. Vzhledem k tomu, že kompilátor zná velikost typu `void *`, je výraz vyhodnocen okamžitě.

## <a name="example"></a>Příklad

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description"></a>Popis

V následujícím příkladu má deklarace **static_assert** obor třídy. **Static_assert** ověří, zda je parametr šablony *prostým starým typem dat* (pod). Kompilátor prověřuje deklaraci **static_assert** , když je deklarována, ale nevyhodnotí parametr *konstanty-Expression* , dokud není vytvořena instance `basic_string` třídy v `main()`.

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

V následujícím příkladu má deklarace **static_assert** rozsah bloku. **Static_assert** ověří, zda je velikost struktury VMPage rovna hodnotě velikosti paměti virtuálního počítače.

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

## <a name="see-also"></a>Viz také

[Kontrolní výraz a uživatelem zadané zprávy (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#error – direktiva (C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Šablony](../cpp/templates-cpp.md)<br/>
[Znaková sada ASCII](../c-language/ascii-character-set.md)<br/>
[Deklarace a definice](declarations-and-definitions-cpp.md)
