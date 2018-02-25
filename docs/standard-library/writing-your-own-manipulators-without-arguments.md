---
title: "Psaní vlastních manipulátorů bez argumentů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: abd4084a7ba4b011d95258867646fac20b5c6572
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="writing-your-own-manipulators-without-arguments"></a>Psaní vlastních manipulátorů bez argumentů
Zápis manipulátory, které nepoužívají argumenty vyžaduje odvození třídy ani používají komplexní makra. Předpokládejme, že tiskárna vyžaduje dvojici \<ESC > [k zadání tučné režimu. Můžete vložit tento pár přímo do datového proudu:  
  
```  
cout <<"regular " <<'\033' <<'[' <<"boldface" <<endl;  
```  
  
 Nebo můžete definovat `bold` manipulator, která vloží znaky:  
  
```  
ostream& bold(ostream& os) {  
    return os <<'\033' <<'[';  
}  
cout <<"regular " <<bold <<"boldface" <<endl;  
```  
  
 Globálně definovaný `bold` funkce trvá `ostream` argument a vrátí odkaz `ostream` odkaz. Není členské funkce nebo přítele protože nepotřebuje přístup k žádné elementy Soukromá třída. `bold` Funkce připojí do datového proudu, protože datový proud `<<` operátor je přetížena tak, aby přijímal typu funkce, pomocí deklaraci, která vypadá přibližně takto:  
  
```  
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))  
{     // call ios_base manipulator  
 (*_Pfn)(*(ios_base *)this);

    return (*this);

}  
```  
  
 Tato funkce slouží k rozšíření jiných přetížené operátory. V takovém případě je následných, `bold` vloží znaků do datového proudu. Funkce je volána, když je vložen do datového proudu, nemusí při tisku sousedících znaků. Tisk může tedy dojít ke zpoždění, kvůli ukládání do vyrovnávací paměti datový proud.  
  
## <a name="see-also"></a>Viz také  
 [Výstupní streamy](../standard-library/output-streams.md)

