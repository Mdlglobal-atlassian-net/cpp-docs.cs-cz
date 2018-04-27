---
title: Používání operátorů extrakce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26dec4b3bdad481e53e88ca2c91c82161de9bf81
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="using-extraction-operators"></a>Používání operátorů extrakce

Operátor extrakce (`>>`), který je naprogramovaných pro všechny standardní datové typy C++, je nejjednodušší způsob, jak získat bajtů z objektu vstupního datového proudu.

Formátovaný text vstupní extraction – operátory závisí na mezera příchozí data hodnot. Toto je nepohodlná, když pole obsahuje více slova nebo když čísla oddělte čárkami. V takovém případě jeden alternativou je pomocí funkce neformátovaný vstupní člen [istream::getline](../standard-library/basic-istream-class.md#getline) číst blok textu s bílými oblasti zahrnuty, pak analyzovat blok s speciální funkce. Další možností je odvozena třídu vstupního datového proudu s členské funkce, jako `GetNextToken`, které můžete volat IStream on Request členy k extrahování a formátování dat znak.

## <a name="see-also"></a>Viz také

[Vstupní streamy](../standard-library/input-streams.md)<br/>
