---
title: Cuserexception – třída
ms.date: 11/04/2016
f1_keywords:
- CUserException
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
ms.openlocfilehash: 72d8537616792859a2b00a1a5cd880ce5eb452bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323434"
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

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
