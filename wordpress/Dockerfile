FROM php:7.4-apache

RUN apt-get update; \
	apt-get install -y --no-install-recommends \
	; \
	rm -rf /var/lib/apt/lists/*

RUN a2enmod rewrite

# Install required and recommended extensions for php for wordpress
RUN apt-get update; \
	 apt-get install -y --no-install-recommends \
		libfreetype6-dev \
		libicu-dev \
		libjpeg-dev \
		libmagickwand-dev \
		libpng-dev \
		libwebp-dev \
		libzip-dev \
  ; \
  \
	docker-php-ext-configure gd \
		--with-freetype \
		--with-jpeg \
		--with-webp \
	; \
	docker-php-ext-install \
		bcmath \
		exif \
		gd \
		intl \
		mysqli \
		zip \
	; 

EXPOSE 80

COPY . /var/www/html

# restart the apache server
CMD ["apache2ctl", "restart"]





