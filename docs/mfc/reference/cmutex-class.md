---
title: CMutex – třída
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 823f38a6292152774f72c97963b9add5d429d2f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508781"
---
# <a name="cmutex-class"></a>CMutex – třída

Představuje "mutex" – synchronizační objekt umožňující jeden vlákno vzájemně exkluzivní přístup k prostředku.

## <a name="syntax"></a>Syntaxe

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|Vytvoří `CMutex` objektu.|

## <a name="remarks"></a>Poznámky

Vzájemně vyloučené přístupy jsou užitečné, pokud najednou pouze jedno vlákno může být povoleno upravovat data nebo jiný řízené prostředek. Například přidání uzlů do propojený seznam je proces, který pouze by měl být povoleno jedno vlákno najednou. Pomocí `CMutex` objekt pro řízení seznamu propojených pouze jedno vlákno najednou můžete získat přístup k seznamu.

Použití `CMutex` objektu, vytvořit `CMutex` objektu, když ho nepotřebují. Zadejte název objektu mutex, chcete čekat na a, která vaše aplikace by měl původně jejím vlastníkem. Po návratu konstruktoru moct mutex. Volání [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) až budete mít přístup k řízenému prostředku.

Alternativní způsob pro použití `CMutex` objekty, je přidat proměnnou typu `CMutex` jako datový člen třídy, které chcete ovládací prvek. Během konstrukce objektu řízené volání konstruktoru `CMutex` datový člen zadáte-li mutex je zpočátku vlastní, název mutex (Pokud se bude používat přes hranice procesu) a požadované atributy zabezpečení.

Pro přístup k prostředkům řídí `CMutex` objekty tímto způsobem, nejprve vytvořte proměnnou jednoho z těchto typů [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo typ [CMultiLock](../../mfc/reference/cmultilock-class.md) v členské funkci přístup váš prostředek. Poté zavolejte zamknout objekt `Lock` členskou funkci (například [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). V tomto okamžiku vašeho vlákna budou buď získat přístup k prostředku, počkejte prostředek, který má být všeobecně dostupné a získat přístup nebo počkejte prostředek uvolnit a vypršení časového limitu, selhání získat přístup k prostředku. V každém případě váš prostředek má byla přístupná takovým způsobem bezpečným pro vlákno. K uvolnění prostředku, použijte zámek objektu `Unlock` členskou funkci (například [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), nebo povolíte zámek objektu spadá mimo rozsah.

Další informace o používání `CMutex` objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

##  <a name="cmutex"></a>  CMutex::CMutex

Konstrukce a pojmenované a nepojmenované `CMutex` objektu.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bInitiallyOwn*<br/>
Určuje, pokud vytváření vlákna `CMutex` objektu původně má přístup k prostředku řídí mutex.

*lpszName*<br/>
Název `CMutex` objektu. Pokud existuje jiný objekt mutex se stejným názvem, *lpszName* musí být zadán, pokud se použije objekt přes hranice procesu. Pokud **NULL**, mutex budou bez názvu. Pokud název odpovídá existující objekt mutex, konstruktoru vytvoří novou `CMutex` objekt, který odkazuje na objekt mutex s tímto názvem. Pokud název odpovídá existující synchronizační objekt, který není objekt mutex, procesu vytváření se nezdaří.

*lpsaAttribute*<br/>
Atributy zabezpečení pro objekt mutex. Úplný popis této struktury viz [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Přístup nebo vydání `CMutex` objektu, vytvořit [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) objektu a volání jeho [Zámek](../../mfc/reference/csinglelock-class.md#lock) a [odemknout](../../mfc/reference/csinglelock-class.md#unlock) Členské funkce. Pokud `CMutex` objektu používá samostatné, zavolejte jeho `Unlock` členskou funkci pro uvolnění.

> [!IMPORTANT]
>  Po vytvoření `CMutex` objektu, použijte [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) zajistit, že mutex již neexistuje. Pokud mutex neočekávaně neexistuje, může to znamenat podvodný procesu je obsazení a může být úmyslem použít mutex závadně. Doporučený postup zabezpečení v tomto případě je zavřít popisovač a pokračovat, jako při vytváření objektu došlo k chybě.

## <a name="see-also"></a>Viz také

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

