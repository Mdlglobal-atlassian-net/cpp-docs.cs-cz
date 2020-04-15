---
title: /Zc:ternary (vynucení pravidel podmiňovacího operátoru)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 7c95f061e195ccf7fef8a6a21d193b257baa5f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335679"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (vynucení pravidel podmiňovacího operátoru)

Povolit vynucení c++ standardní pravidla pro typy a const nebo volatile (cv) kvalifikace druhého a třetího operandů ve výrazu podmíněného operátoru.

## <a name="syntax"></a>Syntaxe

> **/Zc:ternární****-**[ ]

## <a name="remarks"></a>Poznámky

Počínaje Visual Studio 2017 kompilátor podporuje c++ standardní *podmíněný operátor* (**?:**) chování. To je také známé jako *ternární operátor*. C++ Standard vyžaduje ternární operandy splňují jednu ze tří podmínek: operandy musí být stejného typu a **const** nebo **těkavé** kvalifikace (cv-kvalifikace), nebo pouze jeden operand musí být jednoznačně převoditelný na stejný typ a cv-kvalifikace jako ostatní. Nebo jeden nebo oba operandy musí být throw výraz. Ve verzích před Visual Studio 2017 verze 15.5 kompilátor povolené převody, které jsou považovány za nejednoznačné standardem.

Pokud je zadána možnost **/Zc:ternary,** kompilátor odpovídá standardu. Odmítne kód, který nesplňuje pravidla pro odpovídající typy a cv-kvalifikace druhého a třetího operandů.

Možnost **/Zc:ternary** je ve výchozím nastavení vypnutá v sadě Visual Studio 2017. Pomocí **/Zc:ternary** povolte chování přizpůsobení nebo **/Zc:ternary-** explicitně určit předchozí chování kompilátoru nevyhovující. [Možnost /tolerantní-](permissive-standards-conformance.md) implicitně umožňuje tuto možnost, ale může být přepsána pomocí **/Zc:ternary-**.

### <a name="examples"></a>Příklady

Tato ukázka ukazuje, jak může třída, která poskytuje neexplicitní inicializaci z typu, tak převod na typ vést k nejednoznačným převodům. Tento kód je ve výchozím nastavení přijat kompilátorem, ale odmítnut, když je zadán **/Zc:ternary** nebo **/tolerantní-** .

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

Chcete-li tento kód opravit, vytvořte explicitní přetypování na upřednostňovaný běžný typ nebo zabraňte jednomu směru převodu typu. Kompilátor může zabránit v porovnání převodu typu tím, že převod explicitní.

Důležitou výjimkou z tohoto společného vzoru je, pokud je typ operandů jedním `const char*`z `const char16_t*`typů řetězců ukončených null, například , a tak dále. Můžete také reprodukovat efekt s typy polí a typy ukazatelů, které se rozkládají. Chování, když skutečný druhý nebo `?:` třetí operand do je řetězec literál odpovídající typ závisí na použité matné normy jazyka. C++17 změnil sémantiku pro tento případ z C++14. V důsledku toho kompilátor přijme kód v následujícím příkladu pod výchozí **/std:c++14**, ale odmítne jej při zadání **/std:c++ 17**.

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

Chcete-li tento kód opravit, přetypujte jeden z operandů explicitně.

Pod **/Zc:ternary**kompilátor odmítne podmíněné operátory, kde jeden z argumentů je typu **void**a druhý není výraz throw. Běžné použití tohoto vzoru je v ASSERT-jako makra:

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

Typickým řešením je nahradit neprázdný `void()`argument .

Tato ukázka zobrazuje kód, který generuje chybu pod **/Zc:ternary** a **/Zc:ternary-**:

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

Tento kód dříve dal tuto chybu:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

S **/Zc:ternary**, důvod selhání se stává jasnější. Ke generování každého lambda lze použít libovolný z několika konvencí volání definovaných implementací. Kompilátor však nemá žádné pravidlo preference, které by rozluštou možné lambda podpisy. Nový výstup vypadá takto:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Běžný medailon problémy nalezené **parametrem /Zc:ternary** pochází z podmíněných operátorů používaných v metaprogramování šablony. Některé typy výsledků se v rámci tohoto přepínače mění. Následující příklad ukazuje dva případy, kdy **/Zc:ternary** změní typ výsledku podmíněného výrazu v kontextu bez metaprogramování:

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

Typická oprava je `std::remove_reference` použít vlastnost na typ výsledku, kde je potřeba zachovat staré chování.

Další informace o problémech s kondenzací v jazyce Visual C++ naleznete [v tématu Nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku **vlastností Vlastnosti** > konfigurace**C/C++** > **.**

1. Upravte vlastnost **Další možnosti** tak, aby **zahrnovala parametr /Zc:ternary** nebo **/Zc:ternary-** a pak zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](zc-conformance.md)
