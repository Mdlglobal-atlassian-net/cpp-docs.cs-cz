---
title: /Zc:referenceBinding (vynucení pravidel vazby odkazů)
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: b7e297d6fd913ddda4d44a42298a361e314af0b5
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518475"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (vynucení pravidel vazby odkazů)

Pokud je zadána možnost **/Zc: referenceBinding** , kompilátor nepovoluje odkazování nekonstantní hodnoty lvalue na vytvoření vazby na dočasné.

## <a name="syntax"></a>Syntaxe

> **/Zc:referenceBinding**[ **-** ]

## <a name="remarks"></a>Poznámky

Je-li zadán parametr **/Zc: referenceBinding** , kompilátor sleduje oddíl 8.5.3 standardu c++ 11: nepovoluje výrazy, které vážou uživatelem definovaný typ dočasnou na odkaz nekonstantní hodnoty lvalue. Ve výchozím nastavení, nebo pokud je zadán parametr **/Zc: referenceBinding-** , kompilátor umožňuje tyto výrazy jako rozšíření společnosti Microsoft, ale je vydáno upozornění úrovně 4. V případě zabezpečení a přenositelnosti kódu doporučujeme použít parametr **/Zc: referenceBinding**.

Možnost **/Zc: referenceBinding** je ve výchozím nastavení vypnutá. Možnost kompilátoru [/Permissive-](permissive-standards-conformance.md) implicitně nastaví tuto možnost, ale je možné ji přepsat pomocí příkazu **/Zc: referenceBinding-** .

## <a name="example"></a>Příklad

V této ukázce se zobrazuje rozšíření společnosti Microsoft, které umožňuje vytvořit dočasný typ uživatelsky definovaného typu, který je vázán na odkaz, který není const na lvalue.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

int main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Další informace o problémech s kompatibilitou ve vizuálu C++najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránce vlastností **příkazového řádku** **jazyka C/C++**  > .

1. Upravte vlastnost **Další možnosti** tak, aby zahrnovala **/Zc: referenceBinding** a pak zvolte **OK**.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (shoda)](zc-conformance.md)<br/>
