---
title: Konstanty znaků jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 5d87b57726f741cc96f2180de33cae01403786ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326297"
---
# <a name="c-character-constants"></a>Konstanty znaků jazyka C

"Znaková konstanta" je tvořena uzavřením jednoho znaku reprezentovatelné znakové sady do jednoduchých uvozovek (**""**). Znakové konstanty se používají k vyjádření znaků ve [znaková sada spuštění](../c-language/execution-character-set.md).

## <a name="syntax"></a>Syntaxe

*Znaková konstanta*: **"** *c-char pořadí* **.**

**L "** *c-char pořadí* **.**

*c – znak sekvence*: *c-char*

*c – znak sekvence jazyka c-char*

*c-char*: Každý člen zdrojové znakové sady kromě jednoduché uvozovky (**"**), zpětného lomítka (**\\**), nebo znak nového řádku

*řídicí sekvence*

*řídicí sekvence*: *simple-escape-sequence*

*octal-escape-sequence*

*hexadecimal-escape-sequence*

*Simple-escape-sequence*: jeden z **\a \b \f \n \r \t \v**

**\\' \\" \\\ \\?**

*osmičková řídicí sekvence*: **\\** *uveden jako osmičková číslice*

**\\**  *uveden jako osmičková číslice osmičkovými číslicemi*

**\\**  *uveden jako osmičková číslice uveden jako osmičková číslice osmičkovými číslicemi*

*šestnáctková řídicí sekvence*: **\x**  *šestnáctkové číslice*

*šestnáctková řídicí sekvence šestnáctkové číslice*

## <a name="see-also"></a>Viz také:

[Konstanty jazyka C](../c-language/c-constants.md)
