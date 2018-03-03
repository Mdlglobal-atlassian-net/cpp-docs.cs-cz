---
title: C.2 pravidla | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e5efa8d0e7cf4118362b7695bafcd4710b4021f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c2-rules"></a>C.2 Pravidla
Notace je popsané v části 6.1 standardní C. Tento dodatek gramatika ukazuje rozšíření pro gramatika základní jazyk pro direktivy OpenMP C a C++.  
  
 **/\*v jazyce C++ (ISO/IEC 14882:1998)\*/**  
  
 *příkaz seq*:  
  
 *příkaz*  
  
 *OpenMP – direktiva*  
  
 *příkaz seq – příkaz*  
  
 *příkaz seq openmp – direktiva*  
  
 **/\*v C90 (ISO/IEC 9899:1990)\*/**  
  
 *seznam příkazů*:  
  
 *příkaz*  
  
 *OpenMP – direktiva*  
  
 *příkaz seznam příkazů*  
  
 *seznam příkazů openmp – direktiva*  
  
 **/\*v C99 (ISO/IEC 9899:1999)\*/**  
  
 *položka bloku*:  
  
 *deklarace*  
  
 *příkaz*  
  
 *OpenMP – direktiva*  
  
 *příkaz*:  
  
 **/\*standardní příkazy\*/**  
  
 *OpenMP – konstrukce*  
  
 *OpenMP – konstrukce*:  
  
 *paralelní konstrukce*  
  
 *pro konstrukce*  
  
 *části – konstrukce*  
  
 *Single – konstrukce*  
  
 *paralelní pro konstrukce*  
  
 *paralelní části – konstrukce*  
  
 *hlavní construc*  
  
 *Critical – konstrukce*  
  
 *Atomic – konstrukce*  
  
 *seřazené konstrukce*  
  
 *OpenMP – direktiva*:  
  
 *Barrier – direktiva*  
  
 *Flush – direktiva*  
  
 *strukturovaná bloku*:  
  
 *příkaz*  
  
 *paralelní konstrukce*:  
  
 *paralelní – direktiva strukturovaná bloku*  
  
 *paralelní – direktiva*:  
  
 **omp – Direktiva pragma #, – paralelní***paralelní klauzule*optseq *nový řádek*   
  
 *paralelní klauzule*:  
  
 *Jedinečný paralelní klauzule*  
  
 *dat – klauzule*  
  
 *Jedinečný paralelní klauzule*:  
  
 **Pokud (** *výraz* **)**  
  
 **num_threads (** *výraz* **)**  
  
 *pro konstrukce*:  
  
 *pro direktiva iterace – příkaz*  
  
 *pro direktiva*:  
  
 **omp – Direktiva pragma # pro** *klauzuli for*optseq *nový řádek*  
  
 *klauzuli for*:  
  
 *Jedinečný pro klauzuli*  
  
 *dat – klauzule*  
  
 **nowait**  
  
 *Jedinečný pro klauzuli*:  
  
 **řazení**  
  
 **plán (** *plán druh* **)**  
  
 **plán (** *plán druh* **,** *výraz* **)**  
  
 *Typ plánu*:  
  
 **static**  
  
 **dynamic**  
  
 **na základě**  
  
 **modul runtime**  
  
 *konstrukce části*:  
  
 *část oboru části – direktiva*  
  
 *Direktiva části*:  
  
 **části omp – Direktiva pragma #** *části klauzule*optseq *nový řádek*  
  
 *klauzule části*:  
  
 *dat – klauzule*  
  
 **nowait**  
  
 *část oboru*:  
  
 *{oddíl pořadí}*  
  
 *část pořadí*:  
  
 *Direktiva části*opt *strukturovaná bloku*  
  
 *část pořadí část – direktiva strukturovaná bloku*  
  
 *Direktiva části*:  
  
 **část omp – Direktiva pragma #** *nový řádek*  
  
 *Single – konstrukce*:  
  
 *Single – direktiva strukturovaná bloku*  
  
 *Single – direktiva*:  
  
 **omp – Direktiva pragma #, – jeden** *jedním klauzule*optseq *nový řádek*  
  
 *klauzule jedním*:  
  
 *dat – klauzule*  
  
 **nowait**  
  
 *paralelní pro konstrukce*:  
  
 *paralelní pro direktiva iterace – příkaz*  
  
 *paralelní pro direktiva*:  
  
 **omp – Direktiva pragma #, – paralelní pro** *paralelní pro klauzuli*optseq *nový řádek*  
  
 *paralelní pro klauzuli*:  
  
 *Jedinečný paralelní klauzule*  
  
 *Jedinečný pro klauzuli*  
  
 *dat – klauzule*  
  
 *paralelní. části konstrukce*:  
  
 *část oboru paralelní části – direktiva*  
  
 *paralelní části – direktiva*:  
  
 **# – Direktiva pragma omp – paralelní části** *paralelní. oddíly klauzule*optseq *nový řádek*  
  
 *paralelní. oddíly klauzule*:  
  
 *Jedinečný paralelní klauzule*  
  
 *dat – klauzule*  
  
 *master – konstrukce*:  
  
 *hlavní – direktiva strukturovaná bloku*  
  
 *hlavní – direktiva*:  
  
 **hlavní omp – Direktiva pragma #** *nový řádek*  
  
 *Critical – konstrukce*:  
  
 *důležité – direktiva strukturovaná bloku*  
  
 *důležité – direktiva*:  
  
 **omp – Direktiva pragma #, – kritická** *oblast frázi*opt *nový řádek*  
  
 *oblast frázi*:  
  
 *(identifier)*  
  
 *Barrier – direktiva*:  
  
 **barrier omp – Direktiva pragma #** *nový řádek*  
  
 *Atomic – konstrukce*:  
  
 *Atomic – direktiva výraz – příkaz*  
  
 *Atomic – direktiva*:  
  
 **# – Direktiva pragma omp atomic –** *nový řádek*  
  
 *Flush – direktiva*:  
  
 **omp – Direktiva pragma #, – vyprázdnění** *vyprázdnění vars*opt *nový řádek*  
  
 *vyprázdnění vars*:  
  
 *(seznamu proměnné)*  
  
 *seřazené konstrukce*:  
  
 *seřazené – direktiva strukturovaná bloku*  
  
 *seřazené – direktiva*:  
  
 **omp – Direktiva pragma # seřazené** *nový řádek*  
  
 *deklarace*:  
  
 **/\*Standardní deklarace\*/**  
  
 *threadprivate – direktiva*  
  
 *threadprivate – direktiva*:  
  
 **threadprivate omp – Direktiva pragma # (** *seznamu proměnné***)** *nový řádek*   
  
 *data klauzule*:  
  
 **privátní (** *seznamu proměnné* **)**  
  
 **copyprivate (***seznamu proměnné***)**   
  
 **firstprivate (***seznamu proměnné***)**   
  
 **lastprivate (** *seznamu proměnné***)**   
  
 **sdílené (** *seznamu proměnné* **)**  
  
 **Výchozí (sdílené)**  
  
 **Výchozí (none)**  
  
 **snížení (***operátor snížení***:***seznamu proměnné***)**   
  
 **copyin (***seznamu proměnné***)**   
  
 *operátor snížení*:  
  
 *Jeden z*:  **+  \* -& ^ &#124; & & &#124; &#124;**  
  
 **/\*v jazyce C\*/**  
  
 *Proměnná seznamu*:  
  
 *identifikátor*  
  
 *Proměnná seznamu* **,** *identifikátor*  
  
 **/\*v jazyce C++\*/**  
  
 *Proměnná seznamu*:  
  
 *ID – výraz*  
  
 *Proměnná seznamu* **,** *id výrazu*