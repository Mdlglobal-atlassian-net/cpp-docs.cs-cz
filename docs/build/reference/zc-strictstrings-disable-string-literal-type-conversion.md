---
title: "/ Zc: strictstrings (zakázání převodů typů řetězcových literálů) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:strictStrings
- strictStrings
dev_langs:
- C++
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61ae45d6a067b45d625055d92900b17e69a366e7
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (Zakázání převodů typů řetězcových literálů)

-Li zadána, vyžaduje kompilátor striktní `const`-kvalifikace shoda pro ukazatele inicializovat pomocí textové literály.

## <a name="syntax"></a>Syntaxe

> **/Zc:strictStrings**[**-**]

## <a name="remarks"></a>Poznámky

Pokud **/Zc: strictstrings** není zadaný, kompilátor vynucuje standardní C++ `const` kvalifikaci pro textové literály jako typ se pole `const char`' nebo ' pole `const wchar_t`', v závislosti na deklaraci. Textové literály jsou neměnné a pokus o změnit obsah jedné výsledkem chyba narušení přístupu za běhu. Je potřeba deklarovat ukazatel řetězec jako `const` inicializovat pomocí řetězcový literál nebo použijte explicitní `const_cast` k chybě při inicializaci jinou hodnotu než`const` ukazatel. Ve výchozím nastavení nebo pokud **/Zc:strictStrings-** není zadaný, kompilátor nevynucuje standardní C++ `const` kvalifikaci pro řetězec ukazatele inicializovat pomocí textové literály.

**/Zc: strictstrings** možnost je ve výchozím nastavení vypnuta. [/ Projektovou-](permissive-standards-conformance.md) – možnost kompilátoru implicitně nastaví tato možnost, ale můžete přepsat pomocí **/Zc:strictStrings-**.

Použití **/Zc: strictstrings** možnost, aby se zabránilo kompilace nesprávný kód. Tento příklad ukazuje, jak chybu jednoduchý deklarace vede k chybě v době běhu:

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

Pokud používáte `auto` deklarovat ukazatel řetězec, kompilátor vytvoří správný `const` ukazatel deklarace typu pro vás. Pokus o upravovat obsah `const` ukazatel je hlášen kompilátoru za chybu.

> [!NOTE]
> Standardní knihovna C++ v [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] nepodporuje **/Zc: strictstrings** – možnost kompilátoru ladění sestavení. Pokud se zobrazí několik [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) výstupní chyby v buildu, příčinou může být.

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc: strictstrings** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
