FROM python:3.9

# 작업 디렉토리 설정
WORKDIR /app

# 필요한 파일 명시적으로 복사
COPY requirements.txt .
COPY main.py .
COPY todo.json .
COPY templates/ ./templates/
COPY tests/ ./tests/

# 의존성 설치
RUN pip install --no-cache-dir -r requirements.txt

# 비root 사용자 생성 및 권한 설정
RUN adduser --disabled-password --gecos '' appuser
USER appuser

# FastAPI 서버 실행
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "5001"]