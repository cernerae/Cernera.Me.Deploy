ARG react_app_version

FROM cernerae/cernera_me_react_app:${react_app_version} as react

FROM nginx:1.17.3

COPY --from=react /usr/src/app/build /usr/share/nginx/cernera_me

RUN rm /etc/nginx/conf.d/default.conf
COPY default.conf /etc/nginx/conf.d

RUN mkdir -p /etc/ssl/certs
COPY ssl_certs/__cernera_me.crt /etc/ssl
COPY ssl_certs/__cernera_me.key /etc/ssl

RUN chmod 755 /usr/share/nginx/cernera_me -R

EXPOSE 80
EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
