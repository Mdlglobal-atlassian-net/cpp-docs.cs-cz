---
title: Globální funkce kompilátoru modelu COM | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb769cf1419f7a0142a5eeae348ca432f78fb92a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034134"
---
# <a name="compiler-com-global-functions"></a>Globální funkce kompilátoru modelu COM

**Specifické pro Microsoft**

K dispozici jsou následující rutiny:

|Funkce|Popis|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Vyvolá výjimku [_com_error](../cpp/com-error-class.md) v reakci na selhání.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Nahradí výchozí funkci, která se používá pro zpracování chyb modelu COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Převede `BSTR` hodnota, která se `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Převede `char *` hodnota, která se `BSTR`.|

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)<br/>
[Podpora kompilátoru COM](../cpp/compiler-com-support.md)