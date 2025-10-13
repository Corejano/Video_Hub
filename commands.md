celery -A config worker --loglevel=info --pool=solo

redis-server
redis-cli ping