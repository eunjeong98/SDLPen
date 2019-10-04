# SDLPen
## SDLPen 작성방법
### 그리기
void CPenView::OnDraw(CDC* pDC)
{
	CPenDoc* pDoc = GetDocument();
	ASSERT_VALID(pDoc);
	if (!pDoc)
		return;

	// TODO: 여기에 원시 데이터에 대한 그리기 코드를 추가합니다.
	int n = pDoc->m_oa.GetSize();
	CLine* p;
	for (int i = 0; i < n; i++) {
		p = (CLine*)pDoc->m_oa[i];
		p->Draw(pDC);
	}
}

### 마우스 무브
void CPenView::OnMouseMove(UINT nFlags, CPoint point)
{
	if (nFlags == MK_LBUTTON) {
		CLine* p = new CLine(pnt, point, size, col);
		GetDocument()->m_oa.Add(p);
		Invalidate(false);
	}
	pnt = point;
	CView::OnMouseMove(nFlags, point);
}


### 색선택
void CPenView::OnMenuCol()
{
	// TODO: 여기에 명령 처리기 코드를 추가합니다.
	CColorDialog dlg;
	if (dlg.DoModal() == IDOK) {
		col = dlg.GetColor();
	}
}


### 펜크기  조절
void CPenView::OnSize1()
{
	size = 1;
	// TODO: 여기에 명령 처리기 코드를 추가합니다.
}


void CPenView::OnSize16()
{
	// TODO: 여기에 명령 처리기 코드를 추가합니다.
	size = 16;
}


void CPenView::OnSize32()
{
	// TODO: 여기에 명령 처리기 코드를 추가합니다.
	size = 32;
}
