---
title: '/ Zc: ternary (vynutit pravidla podmíněného operátoru)'
ms.date: 3/06/2018
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: cb9a4f8468a9cb57af711cdca36ee343e5092493
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315427"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/ Zc: ternary (vynutit pravidla podmíněného operátoru)

Povolte vynucení pravidel Standard jazyka C++ pro typy a const nebo volatile (cv) kvalifikace druhý i třetí operand v operátoru podmíněného výrazu.

## <a name="syntax"></a>Syntaxe

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>Poznámky

Visual Studio verze 15.3 podporuje kompilátor C++ standardní podmíněné (nebo Ternární) operátor (**?:**) chování. Standard jazyka C++ vyžaduje operandy stejného typu a cv kvalifikaci, nebo pouze jeden operand jednoznačně převoditelné na stejný typ a cv kvalifikace jako druhý nebo jeden nebo oba operandy na výraz throw. Ve verzích před Visual Studio verze 15.5 kompilátor povolené převody, které jsou považovány za nejednoznačné Standard. Když **/Zc: ternary** je zadána možnost, kompilátor odpovídá standardu a odmítne kód, který nesplňuje pravidla pro odpovídající typy a cv kvalifikace druhého a třetího operandu.

**/Zc: ternary** možnost je vypnuto ve výchozím nastavení. Použití **/Zc: ternary** vyhovující chování, povolit nebo **/Zc:ternary-** s ohledem na předchozí chování kompilátoru nonkonformní. [/ Permissive-](permissive-standards-conformance.md) možnost implicitně povolí tuto možnost, ale lze přepsat pomocí **/Zc:ternary-**.

### <a name="examples"></a>Příklady

Tato ukázka předvádí, jak třídu, která obsahuje oba-explicitní inicializace z typu a převod na typ může mít za následek nejednoznačné převody. Tento kód je ve výchozím nastavení akceptuje kompilátor, ale odmítl při **/Zc: ternary** nebo **/ permissive-** určena.

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

Požadované opravě je provést explicitní přetypování upřednostňované společný typ, nebo zabránit tím, že převod explicitní jeden směr převodu z účasti v kompilátoru hledat shoda typu.

Je důležité výjimky tohoto společného modelu při typu operandu je jedním z typů řetězec zakončený hodnotou null, jako například `const char*`, `const char16_t*`, a tak dále. Můžete to také reprodukovat s typy polí a typy ukazatelů, které jsou decay – k. Chování při skutečné druhý nebo třetí operand?: je textový literál odpovídající typu závisí na standardní jazyk použitý. C ++ 17 se změnila sémantiky pro tento případ z C ++ 14. V důsledku toho je přijat kód v následujícím příkladu v části **/std: c ++ 14** (výchozí nastavení kompilátoru), ale je zamítnuto při **/std: c ++ 17** je zadán.

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

Chcete-li vyřešit tento kód, odevzdat jeden z operandů explicitně.

V části **/Zc: ternary**podmíněných operátorů kompilátoru odmítne, kde jeden z argumentů má typ void a druhý není výraz throw. Běžné použití z nich je v makrech podobných kontrolní VÝRAZ:

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

Typických způsobů řešení je jednoduše nahradit argumentů neprázdným void().

Tento příklad ukazuje kód, který generuje chybu v obou **/Zc: ternary** a **/Zc:ternary-**:

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

Tento kód dříve přiřadil k této chybě:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

S **/Zc: ternary** důvod selhání bude jasnější; v architekturách, kde některé z několika, definované implementací konvence volání by mohl použije k vygenerování každé lambda, kompilátor vyjadřuje žádná předvolba mezi nimi podpisy možné lambda, který může odstranit nejednoznačnost. Nový výstup vypadá takto:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Běžné příčiny problémy týkající se přijetí **/Zc: ternary** pochází z použití podmíněného operátoru v šabloně meta programování, se některé typy výsledků v rámci tohoto přepínače. Následující příklad ukazuje dva případy, kdy **/Zc: ternary** změní typ výsledku podmíněný výraz v kontextu meta programování:

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

Typické řešení v takových případech je použít `std::remove_reference` vlastností na výsledek zadejte, kde je potřeba k zachování původního chování.

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc: ternary** nebo **/Zc:ternary-** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)
