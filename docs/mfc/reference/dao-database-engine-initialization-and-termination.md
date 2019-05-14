---
title: Inicializace a ukončování databázového stroje v rozhraní DAO
ms.date: 11/04/2016
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 1b8186627f00105cf782586060b41ae0fb627d76
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611933"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicializace a ukončování databázového stroje v rozhraní DAO

Při použití objektů DAO knihovny MFC rozhraní DAO databázový stroj musí být nejprve inicializovat a pak ukončena, než se ukončí vaše aplikace nebo knihovny DLL. Dvě funkce `AfxDaoInit` a `AfxDaoTerm`, provádění těchto úkolů.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicializace a ukončování databázového stroje v rozhraní DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Inicializuje DAO databázového stroje.|
|[AfxDaoTerm](#afxdaoterm)|Ukončí rozhraní DAO databázového stroje.|

##  <a name="afxdaoinit"></a>  AfxDaoInit

Tato funkce inicializuje DAO databázového stroje.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Poznámky

Ve většině případů nemusíte volat `AfxDaoInit` vzhledem k tomu aplikace automaticky volá ho když ho nepotřebují.

Související informace a příklad volání `AfxDaoInit`, naleznete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

Tato funkce je ukončeno DAO databázový stroj.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Poznámky

Obvykle je potřeba jenom volejte tuto funkce ve standardní knihovnu MFC DLL; aplikace automaticky zavolá `AfxDaoTerm` když je potřeba.

V běžných knihovnách MFC DLL, volání `AfxDaoTerm` před `ExitInstance` funkce, ale po zničení všech objektů knihovny MFC rozhraní DAO.

Související informace naleznete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
