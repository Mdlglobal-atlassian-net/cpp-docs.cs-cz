---
title: Cesty hledání v pravidlech
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: 26b02fa76920f0d0ff380dacd5aa76cfe8e92c79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649966"
---
# <a name="search-paths-in-rules"></a>Cesty hledání v pravidlech

```
{frompath}.fromext{topath}.toext:
   commands
```

## <a name="remarks"></a>Poznámky

Odvozené pravidlo platí pro závislost, pouze v případě, že cesty zadané v závislost přesně odpovídat odvozené pravidlo cesty. Zadejte adresář závislé položky v *frompath* a cílového adresáře v *topath*; nejsou povoleny mezery. Zadejte jenom jednu cestu pro každou příponu. Cesta na jedno rozšíření vyžaduje cestu na druhé. Pokud chcete nastavit aktuální adresář, použijte tečku (.) nebo prázdné složené závorky ({}). Makra mohou představovat *frompath* a *topath*; jsou vyvolány během předběžného zpracování.

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