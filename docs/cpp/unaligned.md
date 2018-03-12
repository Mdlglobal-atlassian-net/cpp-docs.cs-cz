---
title: __unaligned | Microsoft Docs
ms.custom: 
ms.date: 03/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9f30e2b268be6f9398cf0af40d66b786c7cdca9
ms.sourcegitcommit: eb246547c7c9adc7d7ac4083ef09bf6e54dec914
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2018
---
# <a name="unaligned"></a>__unaligned

**Microsoft konkrétní**. Při deklaraci ukazatele s modifikátorem `__unaligned` kompilátor předpokládá, že ukazatel odkazuje na data, která nejsou zarovnána. V důsledku toho vhodné platformy kód se generuje pro zpracování nezarovnané čtení a zapisovala ukazatele.

## <a name="remarks"></a>Poznámky

Tento modifikátor popisuje zarovnání dat řešit ukazatel; ukazatele samotné se předpokládá zarovnána.

Nezbytná pro `__unaligned` – klíčové slovo se liší podle platformy a prostředí. Nepodařilo se správně označit dat může způsobit problémy od penalizacím výkonu až hardwarových chyb. `__unaligned` Modifikátor není platný pro x86 platformy.

Další informace o zarovnání naleznete v následujících tématech:

- [align](../cpp/align-cpp.md)

- [__alignof – operátor](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md)

- [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
