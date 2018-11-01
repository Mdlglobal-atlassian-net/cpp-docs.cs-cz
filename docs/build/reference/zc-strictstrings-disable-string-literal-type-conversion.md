---
title: /Zc:strictStrings (Zakázání převodů typů řetězcových literálů)
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: d0fe7a7aa956ebc7662754b039389983d75ff590
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668712"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (Zakázání převodů typů řetězcových literálů)

-Li zadána, kompilátor, vyžaduje přísné `const`-kvalifikace pro ukazatele inicializované s použitím řetězcové literály.

## <a name="syntax"></a>Syntaxe

> **/Zc:strictStrings**[**-**]

## <a name="remarks"></a>Poznámky

Pokud **/Zc: strictstrings** není zadána, vynucuje kompilátor standard C++ `const` kvalifikace pro řetězcové literály, například typ "pole `const char`" nebo "pole `const wchar_t`" v závislosti na deklaraci. Řetězcové literály jsou neměnné a pokus upravit obsah jednoho způsobí chybu narušení přístupu za běhu. Je třeba deklarovat ukazatel řetězce jako `const` k inicializaci pomocí řetězcového literálu nebo použít explicitní `const_cast` inicializovat non -`const` ukazatele. Ve výchozím nastavení nebo pokud **/Zc:strictStrings-** není zadán, kompilátor nevynucuje standard C++ `const` kvalifikaci pro řetězec ukazatele inicializovaný s použitím řetězcových literálů.

**/Zc: strictstrings** možnost je vypnuto ve výchozím nastavení. [/ Permissive-](permissive-standards-conformance.md) – možnost kompilátoru implicitně nastaví tuto možnost, ale lze přepsat pomocí **/Zc:strictStrings-**.

Použití **/Zc: strictstrings** možnost, chcete-li zabránit kompilaci nesprávného kódu. Tento příklad ukazuje, jak jednoduchá chyba deklarace vede k chybě za běhu:

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

Když **/Zc: strictstrings** je povoleno, stejný kód nahlásí chybu v deklaraci `str`.

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

Pokud používáte `auto` deklarovat ukazatel na řetězec, kompilátor vytvoří správný `const` deklarace typu ukazatele za vás. Pokus upravit obsah `const` ukazatel je vykázán kompilátorem jako chyba.

> [!NOTE]
> Standardní knihovny C++ v sadě Visual Studio 2013 se nepodporuje **/Zc: strictstrings** sestavení – možnost kompilátoru v ladění. Pokud se zobrazí několik [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) chyby ve vašem buildu output, to může být příčinou.

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc: strictstrings** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
