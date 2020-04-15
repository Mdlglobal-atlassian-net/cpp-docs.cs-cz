---
title: Inicializace a ukončování databázového stroje v rozhraní DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 62460e8e55f70b8cb0743f1d044636d25121050d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365895"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicializace a ukončování databázového stroje v rozhraní DAO

DAO se používá s databázemi Accessu a je podporován prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé. Při použití objektů MFC DAO databázový stroj DAO musí být nejprve inicializována a potom ukončena před ukončením aplikace nebo Knihovny DLL. Dvě funkce `AfxDaoInit` `AfxDaoTerm`a , provádět tyto úkoly.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicializace a ukončování databázového stroje v rozhraní DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Inicializuje databázový stroj DAO.|
|[AfxDaoTermín](#afxdaoterm)|Ukončí databázový stroj DAO.|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a>AfxDaoInit

Tato funkce inicializuje databázový stroj DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Poznámky

Ve většině případů není nutné volat, `AfxDaoInit` protože aplikace automaticky volá, když je to potřeba.

Související informace a příklad volání `AfxDaoInit`naleznete v technické [poznámce 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a>AfxDaoTermín

Tato funkce ukončí databázový stroj DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Poznámky

Obvykle stačí volat tuto funkci v běžné knihovně DLL knihovny MFC; aplikace bude automaticky `AfxDaoTerm` volat, když je to potřeba.

V běžných knihovnách DLL knihovny MFC volání `AfxDaoTerm` před `ExitInstance` funkce, ale po všechny objekty Knihovny MFC DAO byly zničeny.

Související informace naleznete [v technické poznámce 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
