---
title: Globální funkce kompilátoru modelu COM
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: ac74270cd020aa66ccc14ff314a00b388a038086
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504417"
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