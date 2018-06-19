---
title: Cesty hledání v pravidlech | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25127377f20de3cb7c7b55e275692eefbf077067
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380398"
---
# <a name="search-paths-in-rules"></a>Cesty hledání v pravidlech
```  
{frompath}.fromext{topath}.toext:  
   commands  
```  
  
## <a name="remarks"></a>Poznámky  
 Odvozené pravidlo platí pro závislost, pouze v případě, že cesty zadané v závislost přesně odpovídat odvozené pravidlo cesty. Zadejte adresář závislé v *frompath* a cílový adresář v *topath*; nejsou povoleny mezery. Zadejte jenom jednu cestu pro každé rozšíření. Na cestu na jedno rozšíření vyžaduje cesta na straně druhé. Pokud chcete nastavit aktuální adresář, použijte tečku (.) nebo prázdný závorky ({}). Makra může představovat *frompath* a *topath*; jsou vyvolány při předběžném zpracování.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
{dbi\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUDBI) $<  
  
{ilstore\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{misc\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{misc\}.c{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{msf\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
  
{bsc\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{mre\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{namesrvr\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $(YUPDB) $<  
  
{src\cvr\}.cpp{$(ODIR)}.obj::  
        $(CC) $(CFLAGS) $<  
```  
  
## <a name="see-also"></a>Viz také  
 [Definice pravidla](../build/defining-a-rule.md)