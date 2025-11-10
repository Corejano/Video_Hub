celery -A config worker --loglevel=info --pool=solo
celery -A config beat -l info

redis-server
redis-cli ping

stripe listen --forward-to localhost:8000/payment/webhook/

# Terminal 1: Django
python manage.py runserver

# Redis(local)
redis-server

# Terminal 2: Celery Worker
celery -A config worker -l INFO

# Terminal 3: Celery Beat
celery -A config beat -l INFO

# Terminal 4: Stripe webhook (для локальной разработки)
stripe listen --forward-to localhost:8000/payment/webhook/