celery -A config worker --loglevel=info --pool=solo
celery -A config beat -l info

redis-server
redis-cli ping

stripe listen --forward-to localhost:8000/payment/webhook/