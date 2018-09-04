---
title: . KÓD | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff2d66cfc79e84c8c4c7cf92e117c9ac8c84a555
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682484"
---
# <a name="code"></a>.CODE

Při použití s [. MODEL](../../assembler/masm/dot-model.md), označuje začátek segmentu kódu.

## <a name="syntax"></a>Syntaxe

> . KÓD [[název]]

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`name`|Volitelný parametr, který určuje název segmentu kódu. Výchozí název je _TEXT pro malý, malý, zkomprimovat a paušální [modely](../../assembler/masm/dot-model.md). Výchozí název je *modulename*_TEXT pro ostatní modely.|

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>
[.DATA](../../assembler/masm/dot-data.md)<br/>