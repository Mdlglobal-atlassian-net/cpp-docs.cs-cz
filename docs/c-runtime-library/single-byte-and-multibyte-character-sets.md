---
title: Jednobajtové a vícebajtové znakové sady | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.character.multibyte
dev_langs:
- C++
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d6c339f1ab2eecfac5f037e711f19d5ee9323fc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="single-byte-and-multibyte-character-sets"></a>Jednobajtové a vícebajtové znakové sady

Znaková sada ASCII definuje znaky v rozsahu 0x00 – 0x7F. Existuje několik dalších znakových sad, především Evropské, které definují znaky v rozsahu 0x00 – 0x7F stejně jako na znaků ASCII, nastavte a také definovat rozšířené znakové sady z 0x80 - 0xFF. Proto je dostačující k reprezentaci znaková sada ASCII, jakož i znakové sady mnoha evropských jazyků 8bitové, jedním znaková sada (SBCS). Ale některé neevropské znakových sad, jako je například japonské Kanji, zahrnují mnoho více znaků, než může být reprezentován ve schématu kódování jednobajtové a vyžadují proto, že vícebajtové znakové sady (MBCS) kódování.

> [!NOTE]
> Mnoho SBCS rutiny v běhové knihovny Microsoft zpracovávat vícebajtové bajtů, znaky a řetězce podle potřeby. Mnoho vícebajtových znakových sad definovat jako část sady ASCII. V mnoha vícebajtových znakových sad každý znak v rozsahu 0x00 – 0x7F je stejný jako znak, který má stejnou hodnotu ve znakové sadě ASCII. V řetězce znaků ASCII a MBCS, například znak hodnoty NULL jeden bajtů (\0) má hodnotu 0x00 a označuje ukončující znak hodnoty null.

Vícebajtové znakové sady může obsahovat jeden bajt a dvoubajtových znaků. Řetězce vícebajtových znaků, proto může obsahovat kombinaci jednobajtové a dvoubajtové znaky. Dva bajtů vícebajtových znaků má úvodní bajt a druhý bajt. V sadě konkrétní vícebajtových znaků úvodní bajty spadá do určitého rozsahu, jako druhé bajty. Pokud tyto rozsahy překrývají, může být nutné vyhodnotit konkrétní kontext k určení, zda je daný bajt funguje jako úvodní bajt nebo druhý bajt.

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
