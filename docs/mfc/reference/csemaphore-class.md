---
title: CSemaphore – třída
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: f2a05963f39393bcc73650beb44c5dbb8e5535ee
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274216"
---
# <a name="csemaphore-class"></a>CSemaphore – třída

Objekt třídy `CSemaphore` představuje "semafor" – synchronizační objekt, který umožňuje omezenému počtu vláken v jednom nebo více procesech přístup a udržuje přehled o počtu vláken aktuálně přístup k určitému zdroji.

## <a name="syntax"></a>Syntaxe

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|Vytvoří `CSemaphore` objektu.|

## <a name="remarks"></a>Poznámky

Semafory jsou užitečné při řízení přístupu ke sdílenému prostředku, který může podporovat jenom omezený počet uživatelů. Aktuální počet `CSemaphore` objektu je počet další uživatele povolená. Když počet dosáhne nuly, všechny pokusí použít na prostředek řídí `CSemaphore` objektu se vloží do fronty systému a počkejte, dokud se buď časový limit nebo počet překročí 0. Maximální počet uživatelů, kteří mohou přistupovat k prostředku, řízené najednou specifikovaném během procesu vytváření `CSemaphore` objektu.

Použití `CSemaphore` objektu, vytvořit `CSemaphore` objektu, když ho nepotřebují. Zadejte název semafor chcete čekat na a, která vaše aplikace by měl původně jejím vlastníkem. Po návratu konstruktoru moct semafor. Volání [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) až budete mít přístup k řízenému prostředku.

Alternativní způsob pro použití `CSemaphore` objekty, je přidat proměnnou typu `CSemaphore` jako datový člen třídy, které chcete ovládací prvek. Během konstrukce objektu řízené volání konstruktoru `CSemaphore` datový člen určující počáteční přístup počet, počet maximální připojení, název semafor (Pokud se bude používat přes hranice procesu) a požadované atributy zabezpečení.

Pro přístup k prostředkům řídí `CSemaphore` objekty tímto způsobem, nejprve vytvořte proměnnou jednoho z těchto typů [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo typ [CMultiLock](../../mfc/reference/cmultilock-class.md) v členské funkci přístup váš prostředek. Poté zavolejte zamknout objekt `Lock` členskou funkci (například [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). V tomto okamžiku vašeho vlákna budou buď získat přístup k prostředku, počkejte prostředek, který má být všeobecně dostupné a získat přístup nebo počkejte prostředek uvolnit a vypršení časového limitu, selhání získat přístup k prostředku. V každém případě váš prostředek má byla přístupná takovým způsobem bezpečným pro vlákno. K uvolnění prostředku, použijte zámek objektu `Unlock` členskou funkci (například [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), nebo povolíte zámek objektu spadá mimo rozsah.

Alternativně můžete vytvořit `CSemaphore` objektu samostatné a k němu přístup explicitně před pokusem o přístup k řízenému prostředku. Tato metoda při přesnější někomu čtení zdrojového kódu, je více náchylné k chybám.

Další informace o tom, jak používat `CSemaphore` objekty, najdete v článku [Multithreading: Jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

##  <a name="csemaphore"></a>  CSemaphore::CSemaphore

Konstrukce a pojmenované a nepojmenované `CSemaphore` objektu.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Parametry

*lInitialCount*<br/>
Použití počáteční počet pro semafor. Musí být větší než nebo rovna 0 a menší než nebo rovna hodnotě *lMaxCount*.

*lMaxCount*<br/>
Maximální využití počet pro semafor. Musí být větší než 0.

*pstrName*<br/>
Název semafor. Je nutné zadat, pokud semafor budou mít přístup přes hranice procesu. Pokud `NULL`, bude objekt musí být pojmenovaná. Pokud název odpovídá existující semafor, konstruktoru vytvoří novou `CSemaphore` objekt, který odkazuje na spolupráci s tímto názvem. Pokud název odpovídá existující synchronizační objekt, který není semafor, procesu vytváření se nezdaří.

*lpsaAttributes*<br/>
Atributy zabezpečení pro objekt pro spolupráci. Úplný popis této struktury viz [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Přístup nebo vydání `CSemaphore` objektu, vytvořit [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) objektu a volání jeho [Zámek](../../mfc/reference/csinglelock-class.md#lock) a [odemknout](../../mfc/reference/csinglelock-class.md#unlock) Členské funkce.

> [!IMPORTANT]
>  Po vytvoření `CSemaphore` objektu, použijte [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) zajistit, že mutex již neexistuje. Pokud mutex neočekávaně neexistuje, může to znamenat podvodný procesu je obsazení a může být úmyslem použít mutex závadně. Doporučený postup zabezpečení v tomto případě je zavřít popisovač a pokračovat, jako při vytváření objektu došlo k chybě.

## <a name="see-also"></a>Viz také:

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
