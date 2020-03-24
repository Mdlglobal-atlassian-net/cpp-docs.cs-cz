---
title: Globální funkce kompilátoru modelu COM
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: c0a9c742ad9dcbb05ed2d78c954d5a597e3b57cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189777"
---
# <a name="compiler-com-global-functions"></a>Globální funkce kompilátoru modelu COM

**Specifické pro společnost Microsoft**

K dispozici jsou následující rutiny:

|Funkce|Popis|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Vyvolá [_com_error](../cpp/com-error-class.md) jako odpověď na selhání.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Nahradí výchozí funkci, která se používá pro zpracování chyb modelu COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Převede hodnotu `BSTR` na `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Převede hodnotu `char *` na `BSTR`.|

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)<br/>
[Podpora kompilátoru COM](../cpp/compiler-com-support.md)
