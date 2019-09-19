---
title: Inicializace a ukončování databázového stroje v rozhraní DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: ccdf2e7b0f31576dddccad016e6b32806cdb82bf
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095889"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicializace a ukončování databázového stroje v rozhraní DAO

Rozhraní DAO se používá s databázemi Access a je podporované prostřednictvím sady Office 2013. 3,6 je finální verze, která je považována za zastaralou. Při použití objektů knihovny MFC rozhraní DAO musí být nejprve inicializován databázový stroj DAO a poté ukončen před ukončením aplikace nebo knihovny DLL. Dvě funkce `AfxDaoInit` a `AfxDaoTerm`, proveďte tyto úkoly.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicializace a ukončování databázového stroje v rozhraní DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Inicializuje databázový stroj DAO.|
|[AfxDaoTerm](#afxdaoterm)|Ukončí databázový stroj DAO.|

##  <a name="afxdaoinit"></a>AfxDaoInit

Tato funkce inicializuje databázový stroj DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Poznámky

Ve většině případů nemusíte volat `AfxDaoInit` , protože aplikace ji v případě potřeby automaticky volá.

Související informace a příklad volání `AfxDaoInit`naleznete v části [technická Poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

Tato funkce ukončí databázový stroj DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Poznámky

Obvykle stačí tuto funkci volat pouze v běžné knihovně MFC DLL; aplikace bude automaticky volat `AfxDaoTerm` , až bude potřeba.

V běžných knihovnách MFC DLL `AfxDaoTerm` volejte `ExitInstance` před funkcí, ale po zničení všech objektů knihovny MFC DAO.

Související informace najdete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
