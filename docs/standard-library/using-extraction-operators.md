---
title: Používání operátorů extrakce
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 1fc6ffd2f033dfe3df60260f734d93b79d6824f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362423"
---
# <a name="using-extraction-operators"></a>Používání operátorů extrakce

Extrakce – operátor (`>>`), který je předem naprogramovaných pro všechny standardní C++ datové typy, je nejjednodušší způsob, jak získat z objektu vstupního datového proudu bajtů.

Formátovaný text vstupní extrakce operátory závisí na prázdný znak pro oddělení příchozí datové hodnoty. To je praktické, když pole obsahuje více slov nebo když čárkou oddělují číslice. V takovém případě jeden alternativou je použití neformátovaný vstupní členskou funkci [istream::getline](../standard-library/basic-istream-class.md#getline) další blok textu s prázdné znaky, které jsou zahrnuty, pak analyzovat blok s speciální funkce. Jinou metodou je odvodit třídu vstupního datového proudu s členskou funkcí, jako `GetNextToken`, které můžete volat členy istream extrahovat a formátování znaková data.

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)<br/>
