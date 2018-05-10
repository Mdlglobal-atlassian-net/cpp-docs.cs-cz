---
title: Používání operátorů extrakce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96dc02c8bcd82c5b26d3cef71aa2085913ea259d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="using-extraction-operators"></a>Používání operátorů extrakce

Operátor extrakce (`>>`), který je naprogramovaných pro všechny standardní datové typy C++, je nejjednodušší způsob, jak získat bajtů z objektu vstupního datového proudu.

Formátovaný text vstupní extraction – operátory závisí na mezera příchozí data hodnot. Toto je nepohodlná, když pole obsahuje více slova nebo když čísla oddělte čárkami. V takovém případě jeden alternativou je pomocí funkce neformátovaný vstupní člen [istream::getline](../standard-library/basic-istream-class.md#getline) číst blok textu s bílými oblasti zahrnuty, pak analyzovat blok s speciální funkce. Další možností je odvozena třídu vstupního datového proudu s členské funkce, jako `GetNextToken`, které můžete volat IStream on Request členy k extrahování a formátování dat znak.

## <a name="see-also"></a>Viz také

[Vstupní streamy](../standard-library/input-streams.md)<br/>
