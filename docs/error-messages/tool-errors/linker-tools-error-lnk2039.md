---
title: Chyba linkerů LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 7712747deb865ec62fa007fcd95ad09630d00cea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194496"
---
# <a name="linker-tools-error-lnk2039"></a>Chyba linkerů LNK2039

Import třídy ref class\<typ >, který je definován v jiném objektu. obj; měla by být buď importovaná, nebo definovaná, ale ne obojí.

Ref class ' <`type`> ' je importována v zadaném souboru. obj, ale je také definována v jiném souboru. obj. Tato podmínka může způsobit chybu modulu runtime nebo jiné neočekávané chování.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ověřte, zda je nutné v jiném souboru. obj definovat '`type`' a ověřit, zda musí být importován ze souboru. winmd.

1. Odeberte buď definici, nebo import.

## <a name="see-also"></a>Viz také

[Chyby a upozornění linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Chyba linkerů LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)
