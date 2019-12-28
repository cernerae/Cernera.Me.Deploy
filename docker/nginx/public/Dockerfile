FROM nginx:1.17.3

COPY --from=cernerae/cernera_me_react_app /usr/src/app/build /usr/share/nginx/cernera_me

RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d

RUN mkdir -p /etc/ssl

EXPOSE 80
EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
