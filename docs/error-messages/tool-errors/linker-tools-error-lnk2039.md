---
title: Chyba linkerů LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 57d0c101358f84816c8d0cf96eb5137833df0b48
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027540"
---
# <a name="linker-tools-error-lnk2039"></a>Chyba linkerů LNK2039

Importuje se referenční třída\<typu > ", která je definována v another.obj; by měla být buď importovaná nebo definovaná, ale ne obojí.

Třída ref class ' <`type`>' se importují v souboru .obj zadaný, ale je také definováno v jiném souboru .obj. K tomuto stavu může způsobit selhání běhového prostředí nebo jiné neočekávané chování.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte, zda "`type`' musí být definován v jiném souboru .obj a zkontrolujte, jestli musí být importovány ze souboru .winmd.

1. Odeberte definici nebo importu.

## <a name="see-also"></a>Viz také:

[Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Chyba linkerů LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)