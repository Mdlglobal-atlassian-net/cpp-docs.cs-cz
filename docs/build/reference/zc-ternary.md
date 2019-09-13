---
title: /Zc:ternary (vynucení pravidel podmiňovacího operátoru)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 5c38a09b92b4173ca962412a413abc283db590ff
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927496"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (vynucení pravidel podmiňovacího operátoru)

Povolte vynucování C++ standardních pravidel pro typy a typ const nebo volatile (CV) pro druhý a třetí operandy ve výrazu podmíněného operátoru.

## <a name="syntax"></a>Syntaxe

> **/Zc:ternary**[ **-** ]

## <a name="remarks"></a>Poznámky

Počínaje verzí Visual Studio 2017 kompilátor podporuje C++ chování standardního *podmíněného operátoru* ( **?:** ). Je také označován jako *Ternární operátor*. Standard C++ vyžaduje, aby Ternární operand splňoval jednu ze tří podmínek: Operandy musí být stejného typu a **const** nebo **volatile** (kvalifikace-CV), nebo pouze jeden operand musí být jednoznačně převeden na stejný typ a kvalifikace CV jako druhý. Nebo jeden nebo oba operandy musí být výrazem throw. Ve verzích před Visual Studio 2017 verze 15,5 kompilátor povolil převody, které jsou považovány za dvojznačné standardem.

Je-li zadána možnost **/Zc: Ternární** , kompilátor odpovídá standardu. Odmítne kód, který nesplňuje pravidla pro odpovídající typy a kvalifikaci CV druhého a třetího operandu.

Možnost **/Zc: Ternární** je ve výchozím nastavení v aplikaci Visual Studio 2017 vypnutá. Použijte parametr **/Zc: Ternární** pro povolení vyhovujícího chování, nebo **/Zc: Ternární-** pro explicitní určení předchozího nevyhovujícího chování kompilátoru. Možnost [/Permissive-](permissive-standards-conformance.md) implicitně povoluje tuto možnost, ale je možné ji přepsat pomocí příkazu **/Zc: Ternární-** .

### <a name="examples"></a>Příklady

Tento příklad ukazuje, jak třída, která poskytuje neexplicitní inicializaci z typu a převod na typ, může vést k nejednoznačným převodům. Tento kód je ve výchozím nastavení přijat kompilátorem, ale odmítnut, pokud je zadán parametr **/Zc: Ternární** nebo **/Permissive-** .

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

Chcete-li tento kód opravit, proveďte explicitní přetypování na preferovaný běžný typ nebo Zabraňte jednomu směru převodu typu. Můžete zachovat, aby kompilátor shodoval s převodem typu, a to tak, že převod bude explicitní.

Důležitou výjimkou z tohoto obecného vzoru je, že typ operandů je jedním z typů řetězců zakončených hodnotou null, například `const char*`, `const char16_t*`a tak dále. Můžete také reprodukování efektu s typy polí a typy ukazatelů, na které se Decay. Chování, když `?:` je skutečný druhý nebo třetí operand řetězcovým literálem odpovídajícího typu, závisí na použitém jazykovém standardu. C++ 17 změnil sémantiku tohoto případu z C++ 14. V důsledku toho kompilátor akceptuje kód v následujícím příkladu v rámci výchozího **/std: c++ 14**, ale při zadání **/std: c++ 17**se ho odmítne.

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

V sekci **/Zc: Ternární**kompilátor odmítne podmíněné operátory, kde jeden z argumentů je typu **void**a druhý není výrazem throw. Běžné použití tohoto vzoru je v makrech podobných výrazu:

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

Typickým řešením je nahradit argument, který není void, pomocí `void()`.

Tento příklad ukazuje kód, který generuje chybu v rámci parametru **/Zc: Ternární** a **/Zc: Ternární-** :

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

Tento kód dříve poskytl tuto chybu:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Pomocí parametru **/Zc: Ternární**se důvod selhání zruší. K vygenerování každého výrazu lambda lze použít kteroukoli z několika konvencí volání definovaných implementací. Kompilátor ale nemá žádné pravidlo předvolby, které by bylo možné rozlišit možné signatury lambda. Nový výstup vypadá takto:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Společný zdroj problémů nalezený pomocí **/Zc: Ternární** pochází z podmíněných operátorů používaných v meta programování šablon. Některé typy výsledků se mění v rámci tohoto přepínače. Následující příklad ukazuje dva případy, kde **/Zc: Ternární** mění typ výsledku podmíněného výrazu v nemeta-programovacím kontextu:

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

Typickou opravou je použití `std::remove_reference` vlastnosti u typu výsledku, kde je to potřeba k zachování starého chování.

Další informace o problémech s kompatibilitou ve vizuálu C++najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **příkazový řádek** .

1. Upravte vlastnost **Další možnosti** tak, aby zahrnovala **/Zc: Ternární** nebo **/Zc: Ternární-** a pak klikněte na **tlačítko OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)
