---
title: "/Zc:ternary (vynucení pravidel podmíněný operátor) | Microsoft Docs"
ms.date: 1/12/2018
ms.technology: cpp-tools
ms.topic: article
f1_keywords: /Zc:ternary
dev_langs: C++
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c2c4f4e17d3cf72284ec68cf10e75824722d5440
ms.sourcegitcommit: ef2a263e193410782c6dfe47d00764263439537c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (vynucení pravidel podmíněný operátor)

Povolte vynucení pravidel C++ Standard pro typy a const nebo volatile (odchylka nákladů) kvalifikace operandů druhý a třetí ve výrazu podmíněný operátor.

## <a name="syntax"></a>Syntaxe

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>Poznámky

Visual Studio verze 15.3 umožňuje podporu kompilátoru C++ standardní podmíněného (nebo Ternární) operátor (**?:**) chování. Standardní C++ vyžaduje buď operandy být stejného typu a odchylka nákladů kvalifikaci, nebo jenom jeden operand být jednoznačně převoditelná na stejného typu a kvalifikace odchylka nákladů jako druhý nebo jeden nebo oba operandy být výraz throw. Ve verzi před Visual Studio verze 15,5 povoleno kompilátor převody, které jsou považovány nejednoznačný standardní. Když **/Zc:ternary** je zadána možnost, kompilátor vyhovuje standardní a kód, který nesplňuje pravidla pro odpovídající typy a odchylka nákladů kvalifikace operandů druhý a třetí odmítne.

**/Zc:ternary** možnost je ve výchozím nastavení vypnuta. Použití **/Zc:ternary** vyhovující chování, povolit nebo **/Zc:ternary-** explicitně zadat předchozí chování kompilátoru nonkonformní. [/ Projektovou-](permissive-standards-conformance.md) možnost umožňuje **/Zc:ternary**. 

### <a name="examples"></a>Příklady

Tento příklad ukazuje, jak třídu, která obsahuje i jiné explicitním inicializačním z typu a převod na typ může vést k nejednoznačné převody. Tento kód je ve výchozím nastavení přijat kompilátor, ale odmítl při **/Zc:ternary** nebo **/ projektovou-** je zadán.

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

Oprava požadované je provést explicitní přetypování upřednostňovaný typ běžné nebo zabránění v jednom směru převod účast v kompilátoru hledat odpovídající typ tím, že explicitní převod.

Výjimku důležité tento běžný vzor je, když typ operandy je jeden z typů řetězce ukončené hodnotou null, například `const char*`, `const char16_t*`a tak dále. To může reprodukujte s typy polí a ukazatel typy, které budou decay k. Chování při skutečné druhý nebo třetí operand pro?: je řetězcový literál odpovídající typu závisí na standardní jazyk použitý. C ++ 17 změnil sémantiku pro tento případ z C ++ 14. V důsledku toho byla přijata kód v následujícím příkladu v části **/std: c ++ 14** (výchozí nastavení kompilátoru), ale je odmítnut při **/std: c ++ 17** je zadán.

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

Chcete-li odstranit tento kód, odevzdat jeden z operandy explicitně.

V části **/Zc:ternary**, podmíněné operátory kompilátoru odmítne, kde jeden z argumentů je typ void a dalších není throw výraz. Běžně se používají tyto je v makra ASSERT jako:

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

Typické řešením je jednoduše nahraďte void() argument není void.

Tento příklad ukazuje kód, který generuje chybu v obou **/Zc:ternary** a **/Zc:ternary-**:

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

Tento kód dříve jste dali k této chybě:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

S **/Zc:ternary** důvod selhání stane jasnější; na architektury, kde některé z několika definované implementací volání konvencí může generovat každé lambda, kompilátor nevyjadřuje není nastavena žádná předvolba mezi nimi který může odstranit nejednoznačnost podpisy možné lambda. Nové výstup vypadá takto:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Zdroj běžné problémy související s přijetím **/Zc:ternary** pochází z použití podmíněný operátor v šabloně meta-programování, protože některé typy výsledků v rámci tohoto přepínače změnu. Následující příklad ukazuje dva případy, kdy **/Zc:ternary** změní typ výsledku podmíněného výraz v kontextu meta programování:

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

Typické řešením v takových případech je pro použití `std::remove_reference` znak na výsledek zadejte, kde je třeba zachovat původní chování.

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc:ternary** nebo **/Zc:ternary-** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)  
