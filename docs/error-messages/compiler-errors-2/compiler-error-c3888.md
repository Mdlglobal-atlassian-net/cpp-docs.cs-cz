---
title: Chyba kompilátoru C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 40156dfaad5965d30a32d3aa2ac574a5f91999ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176401"
---
# <a name="compiler-error-c3888"></a>Chyba kompilátoru C3888

' name ': typ const přidružený k tomuto datovému členu literálu není C++podporován na/CLI

*Název* datového členu deklarovaný s klíčovým slovem [Literal](../../extensions/literal-cpp-component-extensions.md) je inicializován s hodnotou, kterou kompilátor nepodporuje. Kompilátor podporuje pouze konstanty integrálního, výčtového nebo řetězcového typu. Pravděpodobná příčina chyby **C3888** je, že datový člen je inicializován s polem bajtů.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ověřte, zda je deklarovaný datový člen deklarovaného literálu podporovaným typem.

## <a name="see-also"></a>Viz také

[literal](../../extensions/literal-cpp-component-extensions.md)
