---
title: Chyba Linkerů LNK2039 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac4fdde90911427a1a193bfb6f3a950a7bdcf180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081790"
---
# <a name="linker-tools-error-lnk2039"></a>Chyba linkerů LNK2039

Importuje se referenční třída\<typu > ", která je definována v another.obj; by měla být buď importovaná nebo definovaná, ale ne obojí.

Třída ref class ' <`type`>' se importují v souboru .obj zadaný, ale je také definováno v jiném souboru .obj. K tomuto stavu může způsobit selhání běhového prostředí nebo jiné neočekávané chování.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte, zda "`type`' musí být definován v jiném souboru .obj a zkontrolujte, jestli musí být importovány ze souboru .winmd.

1. Odeberte definici nebo importu.

## <a name="see-also"></a>Viz také

[Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Chyba linkerů LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)