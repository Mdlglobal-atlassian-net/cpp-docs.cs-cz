---
title: Vstupní výstupní datové proudy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51a7a9aff4f77444bbec46a9739fae91cac3c104
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845928"
---
# <a name="inputoutput-streams"></a>Vstupní/výstupní datové proudy

`basic_iostream`, který je definován v záhlaví souboru \<IStream on Request >, je šablona třídy pro objekty, které obě zpracovat vstup a výstup znakový vstupně-výstupní datové proudy.

Existují dvě definice TypeDef, které definují specializací znak specifické `basic_iostream` a vám pomohou lépe kód: `iostream` (Nezaměňovat s soubor hlaviček \<iostream >) je vstupně-výstupní datový proud, který je založen na `basic_iostream<char>`; `wiostream` je vstupně-výstupní datový proud, který je založen na `basic_iostream<wchar_t>`.

Další informace najdete v tématu [basic_iostream – třída](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md), a [wiostream](../standard-library/basic-iostream-class.md).

Odvozující z `basic_iostream` je šablona třídy `basic_fstream`, který se používá k vysílání znak dat do a z soubory.

Existují také – definice TypeDef, zadejte znak konkrétní specializací `basic_fstream`. Jsou `fstream`, což je vstupně-výstupní datový proud, který je založen na `char`, a `wfstream`, což je vstupně-výstupní datový proud, který je založen na `wchar_t`. Další informace najdete v tématu [basic_fstream – třída](../standard-library/basic-fstream-class.md), [fstream](../standard-library/basic-fstream-class.md), a [wfstream](../standard-library/basic-fstream-class.md). Pomocí těchto – definice TypeDef je nutné zahrnout soubor hlaviček \<fstream >.

> [!NOTE]
> Když `basic_fstream` objekt se používá k provádění vstupně-výstupní soubor, i když zdrojová vyrovnávací paměť obsahuje samostatně určený pozice pro čtení a zápis, aktuální vstup a aktuální umístění výstupu, jsou svázané společně, a proto přesune čtení některá data umístění výstupu.

Šablona třídy `basic_stringstream` a jeho běžné specializace `stringstream`, se často používají k práci s objekty datových proudů vstupně-výstupních operací vložení a extrahovat textová data. Další informace najdete v tématu [basic_stringstream – třída](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Viz také

[stringstream –](../standard-library/basic-stringstream-class.md)<br/>
[basic_stringstream – třída](../standard-library/basic-stringstream-class.md)<br/>
[\<sstream – >](../standard-library/sstream.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
