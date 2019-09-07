---
title: Šablony ref ClassesC++(/CX)
ms.date: 01/22/2017
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
ms.openlocfilehash: 3e9c233b5227b4ad86eb632db740001bc2a3a8bd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740854"
---
# <a name="template-ref-classes-ccx"></a>Šablony ref ClassesC++(/CX)

C++šablony nejsou publikovány do metadat, a proto nemohou mít v programu veřejné nebo chráněné přístupnosti. V programu můžete samozřejmě používat standardní C++ šablony interně. Kromě toho můžete definovat soukromou referenční třídu jako šablonu a deklaraci explicitně specializované šablony ref class jako soukromý člen ve veřejné referenční třídě.

## <a name="authoring-ref-class-templates"></a>Vytváření šablon referenčních tříd

Následující příklad ukazuje, jak deklarovat soukromou referenční třídu jako šablonu a také jak deklarovat standardní C++ šablonu a jak je deklarovat jak jako členy veřejné referenční třídy. Všimněte si, že C++ standardní šablona může být specializovaná typem prostředí Windows Runtime, v tomto případě Platform:: String ^.

[!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]

## <a name="see-also"></a>Viz také:

[Systém typů (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
