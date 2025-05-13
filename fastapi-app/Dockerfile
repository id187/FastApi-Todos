FROM python:3.9

# 작업 디렉토리 설정
WORKDIR /app

# 필요한 파일 명시적으로 복사
COPY requirements.txt .
COPY main.py .
COPY todo.json .
COPY templates/ ./templates/
COPY tests/ ./tests/
COPY prometheus/ ./prometheus/

# 의존성 설치 및 비root 사용자 생성
RUN pip install --no-cache-dir -r requirements.txt && \
    adduser --disabled-password --gecos '' appuser

# 비root 사용자로 실행
USER appuser

# FastAPI 서버 실행
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "5001"]