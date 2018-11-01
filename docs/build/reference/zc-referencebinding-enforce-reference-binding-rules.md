---
title: '/ Zc: referencebinding (vynucení pravidel vazby referencí)'
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
ms.openlocfilehash: baf2106f015a4e8557cb8469d300709694e06d84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428324"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/ Zc: referencebinding (vynucení pravidel vazby referencí)

Když **/Zc: referencebinding** je zadána možnost, kompilátor neumožňuje nekonstantní l-odkaz k vytvoření vazby dočasné.

## <a name="syntax"></a>Syntaxe

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>Poznámky

Pokud **/Zc: referencebinding** není zadán, kompilátor následuje oddíl 8.5.3 standardu C ++ 11 a neumožňuje výrazy, kteří jsou navázáni uživatelem definovaného typu dočasný odkaz na nekonstantní l-hodnoty. Ve výchozím nastavení nebo pokud **/Zc:referenceBinding-** není zadán, kompilátor umožňuje tyto výrazy jako rozšíření společnosti Microsoft, ale je vydáno upozornění úrovně 4. Zabezpečení kódu, přenositelnost a shoda, doporučujeme použít **/Zc: referencebinding**.

**/Zc: referencebinding** možnost je vypnuto ve výchozím nastavení. [/ Permissive-](permissive-standards-conformance.md) – možnost kompilátoru implicitně nastaví tuto možnost, ale lze přepsat pomocí **/Zc:referenceBinding-**.

## <a name="example"></a>Příklad

Tento příklad ukazuje rozšíření společnosti Microsoft, který umožňuje dočasný uživatelem definovaného typu vázat na nekonstantní l-odkaz.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

void main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc: referencebinding** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
