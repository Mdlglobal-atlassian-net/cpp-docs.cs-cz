---
title: Cuserexception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71d2be1c00e518597a5d5121d7a53544bd29067f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419656"
---
# <a name="cuserexception-class"></a>Cuserexception – třída

Vyvoláno ukončení operace koncového uživatele.

## <a name="syntax"></a>Syntaxe

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>Poznámky

Použít `CUserException` Pokud chcete použít mechanismus výjimek throw nebo catch pro konkrétní aplikaci výjimky. "User" v názvu třídy může být interpretován jako "Moje uživatelské udělala něco výjimečných, že je potřeba zpracovat."

A `CUserException` obvykle dojde po volání metody globální funkce `AfxMessageBox` upozornit uživatele, operace se nezdařila. Zápis obslužné rutiny výjimky, při zpracování výjimek speciálně, protože uživatel obvykle má už byly oznámeny chyby. Rozhraní vyvolá tuto výjimku v některých případech. Vyvolání `CUserException` sami, upozornit uživatele a potom voláním funkce globální `AfxThrowUserException`.

V následujícím příkladu funkce, který obsahuje operace, které může selhat, zobrazí uživateli výstrahu a vyvolá výjimku `CUserException`. Volání funkce zachytí výjimku a to všechno zvládne speciálně:

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

Další informace o používání `CUserException`, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

[Csimpleexception –](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
