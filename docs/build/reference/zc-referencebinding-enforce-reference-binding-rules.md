---
title: "/Zc:referenceBinding (vynucení pravidel vazby odkaz) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8e3b10f5b2108a4c0e29d802951015749775a27
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (vynucení pravidel vazby odkaz)

Když **/Zc:referenceBinding** je zadána možnost, kompilátor neumožňuje bez const lvalue odkaz pro vazbu do dočasného.

## <a name="syntax"></a>Syntaxe

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>Poznámky

Pokud **/Zc:referenceBinding** je zadán, kompilátor postupuje podle části 8.5.3 C ++ 11 standardní a neumožňuje výrazů, které uživatelsky definovaný typ. dočasné vytvořit vazbu na jiný const lvalue odkaz. Ve výchozím nastavení nebo pokud **/Zc:referenceBinding-** není zadaný, kompilátor umožňuje tyto výrazy jako Microsoft rozšíření, ale se objeví upozornění úroveň 4. Zabezpečení kódu, přenositelnost a shoda, doporučujeme použít **/Zc:referenceBinding**.

**/Zc:referenceBinding** možnost je ve výchozím nastavení vypnuta. [/ Projektovou-](permissive-standards-conformance.md) – možnost kompilátoru implicitně nastaví tato možnost, ale můžete přepsat pomocí **/Zc:referenceBinding-**.

## <a name="example"></a>Příklad

Tento příklad ukazuje Microsoft linku, která umožňuje dočasného typu uživatelem definované bylo vázané na jiný const lvalue odkaz.

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

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc:referenceBinding** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
